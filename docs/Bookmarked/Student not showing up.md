Some students are not showing up on Onshelf.
1. Paige Sandoval
2. Audrey Carr
3. Braxton Jones

#### Students
###### Paige Sandoval
Student table: not exists
Classlink user id: cm6alzm1l0056u33qvmq9r7rn
SID: 84085

###### Audrey Carr
Student table: not exists
Classlink user id: cm0qvan7602gq4xbgyer3wbwj
SID: 67800

###### Braxton Jones
Student table: 39094
Classlink user id: cm0gskqh80h384x40ud2dw4x6
SID: 71356

#### Campus
###### Canyon Int
ID: 111
Entity id: Entity_9

#### Reason
The Students Paige Sandoval and Audrey Carr does not exists in data base.

The student Broxton Jones exists in database but is in wrong campus than the classlink data. Specifically, the student is linked to Greenway Int instead of Canyon Int.

#### Fix
I have inserted the students, Paige Sandoval and Audrey Carr, and also assigned to parent.
What should be done for the student Braxton Jones?


### Queries
`insert into "Parent" ("userId", email, "familyName", "givenName", phone, sms, "sourcedId", address)`

`select null as userId, case when cu2.EMAIL = '' then null ELSE lower(cu2.email) end as email, cu2."familyName", cu2."givenName", cu2.phone, cu2.sms, cu2.identifier , null as address`

`from "ClasslinkUser" cu`

`join "Student" s on s."sourcedId" = cu.identifier`

`join "ClasslinkAgent" ca on ca."userId" = cu.id`

`join "ClasslinkUser" cu2 on cu2."sourcedId" = ca."sourcedId"`

`left join "Parent" p on lower(p.email) = lower(cu2.email )`

`where (cu.id = 'cm6alzm1l0056u33qvmq9r7rn'`

`or cu.id = 'cm0qvan7602gq4xbgyer3wbwj')`

`and cu2.email <> 'jhernandez@splendoraisd.org'`

  

`insert into "_ParentToStudent" ("A", "B")`

`select p.id, s.id`

`from "ClasslinkUser" cu`

`join "Student" s on s."sourcedId" = cu.identifier`

`join "ClasslinkAgent" ca on ca."userId" = cu.id`

`join "ClasslinkUser" cu2 on cu2."sourcedId" = ca."sourcedId"`

`left join "Parent" p on lower(p.email) = lower(cu2.email )`

`where (cu.id = 'cm6alzm1l0056u33qvmq9r7rn'`

`or cu.id = 'cm0qvan7602gq4xbgyer3wbwj')`

`and cu2.email <> 'jhernandez@splendoraisd.org'`