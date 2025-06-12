Archer city campus have more books than should be.

**Elementary ID:** 119
**ISD Campus ID**: 120

**Elementary School**
Total books: 0

**ISD Campus ID**
Books: 18027
Distinct ISBN 10 books: 14627
Distinct ISBN 13 books: 14705
Verified books: 1777
Not verified books: 16250

###### Case for the title "The Floating Island"
In Title table
Count: 10
Verified: 6

###### Reason
3400 books have ISBN 10 as null
3322 books have ISBN 13 as null

###### Final
The catalogue uploaded have duplicate books and books with same name and different ISBNs. That is why we can see multiple duplicates of many books.
Specifically in case of the title "The Floating Island", the excel sheet have the title twice with different ISBNs(978-0-7653-0867-2 and 978-1-41569334-6).
The ISBN "978-1-41569334-6" is not found on ISBNDB, but sheet have the title and author for same, so the title is inserted in database with the info in sheet.
We do have logic to import the ISBN 10 and ISBN 13 from the source is either is not provided and insert to database, but in current case the ISBN was invalid and not found on source, that is why the ISBN 10 and ISBN 13 field are null.

###### Slack response
The catalogue uploaded have duplicate books and books with same name and different ISBNs. That is why we can see multiple duplicates of many books.
Specifically in case of the title "The Floating Island", the excel sheet have the title twice with different ISBNs(978-0-7653-0867-2 and 978-1-41569334-6).
The ISBN "978-1-41569334-6" is not found on ISBNDB, but sheet have the title and author for same, so the title is inserted in database with the info in sheet.
We do have logic to import the ISBN 10 and ISBN 13 from the source is either is not provided and insert to database, but in current case the ISBN was invalid and not found on source, that is why the ISBN 10 and ISBN 13 field are null.
As for the possible fix 
1. We can delete the catalogue and clean the sheet and re-upload.
2. We can delete duplicate title and author books from campus and keep the ones with correct ISBNs.

#### Queries
`-- check the books in archer city`
`select *`

`from "Campus" c`

`where "name" ilike '%archer%'`

`select count(distinct t.isbn13)`

`from "Book" b`

`join "Title" t on t.id = b."sourceTitleId"`

`where "campusId" = 120`

`select t.isbn10 , count(*)`

`from "Book" b`

`join "Title" t on t.id = b."sourceTitleId"`

`where "campusId" = 120`

`group by t.isbn10`

`having count(*) > 1`

`select t."isVerified" , count(*)`

`from "Book" b`

`join "Title" t on t.id = b."sourceTitleId"`

`where "campusId" = 120`

`group by t."isVerified"`

`select t.title , t.isbn , t.isbn10 , t.isbn13`

`from "Title" t`

`where t.title ilike '%floating island%'`

`select t.isbn , t.isbn10, ibr.id , ibh."campusId" , ibh."createdAt" , ibh."fileName"`

`from "Title" t`

`join "Book" b on b."sourceTitleId" = t.id`

`join "ImportedBooksRow" ibr on ibr.id = b."importedBooksRowId"`

`join "ImportedBooksHeader" ibh on ibr."importedBooksHeaderId" = ibh.id`

`where t.title ilike '%floating island%'`

`-- and t.isbn10 isnull`

`and b."campusId" = 120`