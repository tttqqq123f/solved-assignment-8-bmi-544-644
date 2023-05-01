Download Link: https://assignmentchef.com/product/solved-assignment-8-bmi-544-644
<br>
Using Java or Python, write a program to return the courses and sections taught by instructors in the student database.

Instructors should be ordered by last name; courses are to be ordered by section then course number with the course description.

<strong><em>Only simple select statements may be used; table joins are not permitted for this exercise.</em></strong>  You will need to loop through query results to build the query for the next table.

The student database is on a MySQL server at hosted by Amazon Web Services.

<strong><em>Note that the host has changed from the lecture.</em></strong>

Access information is:

host: bmi544.ctqoiylcmh5t.us-west-2.rds.amazonaws.com

database: student

user: bmi544

password: 17bmi544

port: 3306

Output for the first two instructors should look like

Instructor: Hon Rick Chow

Instructor: Dr Marilyn Frantzen

Course 25 Section 1: Intro to Programming

Course 25 Section 9: Intro to Programming

Course 120 Section 1: Intro to Java Programming

Course 122 Section 3: Intermediate Java Programming

Course 125 Section 2: JDeveloper

Course 132 Section 1: Basics of Unix Admin

Course 135 Section 4: Unix Tips and Techniques

Course 145 Section 1: Internet Protocols

Course 230 Section 1: Intro to Internet

Course 350 Section 3: JDeveloper Lab




Return your program and the program’s output as attachments.

Hints:

Include exception handling; it’ll help you find out what went wrong where and why.

Java hints:

Use the appropriate result set method for the datatype, such as rs.getInt() and rs.getString().

Python hints:

Nested queries need a buffered cursor:

cnx.cursor(buffered=True)

A varchar datatype may be returned as a tuple.  If that occurs, you can access it through the first element, as in

desc[0]

Table information and the database schema are on the following pages.

Relevant table information

instructor

+—————-+————–+——+—–+———+——-


| Field          | Type         | Null | Key | Default | Extra |

+—————-+————–+——+—–+———+——-


| instructor_id  | decimal(8,0) | NO   | PRI | NULL    |       |

| salutation     | varchar(5)   | YES  |     | NULL    |       |

| first_name     | varchar(25)  | YES  |     | NULL    |       |

| last_name      | varchar(25)  | YES  |     | NULL    |       |

| street_address | varchar(50)  | YES  |     | NULL    |       |

| zip            | varchar(5)   | YES  |     | NULL    |       |

| phone          | varchar(15)  | YES  |     | NULL    |       |

| created_by     | varchar(30)  | NO   |     | NULL    |       |

| created_date   | date         | NO   |     | NULL    |       |

| modified_by    | varchar(30)  | NO   |     | NULL    |       |

| modified_date  | date         | NO   |     | NULL    |       |

+—————-+————–+——+—–+———+——-





section

+—————–+————–+——+—–+———+——-


| Field           | Type         | Null | Key | Default | Extra |

+—————–+————–+——+—–+———+——-


| section_id      | decimal(8,0) | NO   | PRI | NULL    |       |

| course_no       | decimal(8,0) | NO   | MUL | NULL    |       |

| section_no      | decimal(3,0) | NO   | MUL | NULL    |       |

| start_date_time | date         | YES  |     | NULL    |       |

| location        | varchar(50)  | YES  |     | NULL    |       |

| instructor_id   | decimal(8,0) | NO   | MUL | NULL    |       |

| capacity        | decimal(3,0) | YES  |     | NULL    |       |

| created_by      | varchar(30)  | NO   |     | NULL    |       |

| created_date    | date         | NO   |     | NULL    |       |

| modified_by     | varchar(30)  | NO   |     | NULL    |       |

| modified_date   | date         | NO   |     | NULL    |       |

+—————–+————–+——+—–+———+——-





course

+—————+————–+——+—–+———+——-


| Field         | Type         | Null | Key | Default | Extra |

+—————+————–+——+—–+———+——-


| course_no     | decimal(8,0) | NO   | PRI | NULL    |       |

| description   | varchar(50)  | NO   |     | NULL    |       |

| cost          | decimal(9,2) | YES  |     | NULL    |       |

| prerequisite  | decimal(8,0) | YES  | MUL | NULL    |       |

| created_by    | varchar(30)  | NO   |     | NULL    |       |

| created_date  | date         | NO   |     | NULL    |       |

| modified_by   | varchar(30)  | NO   |     | NULL    |       |

| modified_date | date         | NO   |     | NULL    |       |

+—————+————–+——+—–+———+——-


The Student Database contains the following tables:




course (<u>course_no</u>, description, cost, prerequisite, created_by, created_date, modified_by, modified_date) *prerequisite FK course




section (<u>section_id</u>, course_no, section_no, start_date_time, location, instructor_id, capacity, created_by, created_date, modified_by, modified_date)*instructor_id FK instructor, course_no FK course




student (<u>student_id</u>, salutation, first_name, last_name, street_address, zip, phone, employer, registration_date, created_by, created_date, modified_by, modified_date)*zip FK zipcode




enrollment (<u>student_id, section_id</u>, enroll_date, final_grade, created_by, created_date, modified_by, modified_date) *student_id FK Student, section_id FK section




instructor (<u>instructor_id</u>, salutation, first_name, last_name, street_address, zip, phone, created_by, created_date, modified_by, modified_date) *zip FK zipcode




zipcode (<u>zip</u>, city, state, created_by, created_date, modified_by, modified_date)




grade_type (<u>grade_type_code</u>, description, created_by, created_date, modified_by, modified_date)




grade_type_weight (<u>section_id, grade_type_code</u>, number_per_section, percent_of_final_grade, drop_lowest, created_by, created_date, modified_by, modified_date)  *section_id FK section, grade_type_code FK grade_type




grade (<u>student_id, section_id, grade_type_code, grade_code_occurrence</u>, numeric_grade, comments, created_by, created_date, modified_by, modified_date)*student_id, section_id FK enrollment, section_id, grade_type_code FK grade_type_weight




grade_conversion (<u>letter_grade</u>, grade_point, max_grade, min_grade, created_by, created_date, modified_by, modified_date)










***** Many thanks to Alex Morrison and Alice Rischert in “Oracle SQL Interactive Workbook” for creating this schema and dataset.





