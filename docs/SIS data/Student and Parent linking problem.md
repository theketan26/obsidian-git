### Key
Issue here was parent do exists in parent table but are not linked to student. 
The reason is still unknown but it is fixed indeed.





#### Query
**It includes null value emails to all the students as well so we have to improve**

begin;

create table studentlink(psid text, ssid text);



insert into studentlink

select ca."sourcedId", cu."sourcedId"

from "ClasslinkUser" cu

join "ClasslinkAgent" ca on ca."userId" = cu.id

where cu.status = 'active';

  

  

with ids as (

select s.id as sid, p.id as pid

from (

select sl.ssid as ssid, email

from "ClasslinkUser" cu

join studentlink sl on cu."sourcedId" = sl.psid

) as tolink

join "Student" s on s."sourcedId" = tolink.ssid

join "Parent" p on p.email = tolink.email

)

  

insert into "_ParentToStudent"

select ids.pid, ids.sid

from ids

left join "_ParentToStudent" pts on (pts."A" = ids.pid and pts."B" = ids.sid)

where pts."A" is null

on conflict do nothing

  

  

  

select *

from "_ParentToStudent" pts

join "Student" s on pts."B" = s.id

where pts."A" = 239682

  

drop table studentlink;

  

rollback;