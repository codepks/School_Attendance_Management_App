======================================================================================================================================================================
                                                                  DATABASE SCHEMA
======================================================================================================================================================================

//Attendance Schema<br>
//  The date will keep on incrementing and _id will change too<br>
{<br>
  "_id": ObjectId("..."), <br>
  "date": ISODate("..."), // Date of the attendance record<br>
  "status": "present" // Attendance status (present/absent/tardy/etc.)<br>
}<br>
//Student and class would be linked to above class using lookup and aggregrator<br>

//Student Schema<br>
//1. We will have the student-centric entries<br>
//2. Therefor we will have classes allotted to student and not the other way around<br>
//3. This also takes care of the culture as followed in colleges<br>

{<br>
  "_id": ObjectId("..."), // Unique ID for the student<br>
  "name": "John Doe", // Full name of the student<br>
  "email": "john.doe@example.com", // Email address of the student<br>
  "dob": ISODate("2005-01-01"), // Date of birth of the student<br>
  "gender": "male", // Gender of the student<br>
  "phone": "+1 555-123-4567", // Phone number of the student<br>
  "address": {<br>
    "street": "123 Main St.",<br>
    "city": "Any-town",<br>
    "state": "CA",<br>
    "zip": "12345"<br>
  }, // Address of the student<br>
  "enrollment_date": ISODate("2020-09-01"), // Date when the student enrolled in the school<br>
}<br>


//Class Schema<br>
//This schema is where both the teachers and students meet<br>

{<br>
  "_id": ObjectId("..."), // Unique ID for the class<br>
  "name": "Chemistry 101", // Name of the class<br>
  "teacher_id": ObjectId("..."), // ID of the teacher for the class<br>
  "start_time": ISODate("2023-05-01T09:00:00Z"), // Start time of the class<br>
  "end_time": ISODate("2023-05-01T10:30:00Z"), // End time of the class<br>
  "students": [<br>
    {<br>
      "student_id": ObjectId("..."), // ID of a student in the class<br>
      "enrollment_date": ISODate("2020-09-01") // Date when the student enrolled in the class<br>
    },<br>
    {<br>
      "student_id": ObjectId("..."),<br>
      "enrollment_date": ISODate("2020-09-01")<br>
    },<br>
    // ... additional students in the class ...<br>
  ]<br>
}<br>

    Input fetched to the software by the school<br>
    1. List of students enrolled with their class room name and their personal details<br>
    2. An updated time table <br>
    3. List of teachers and classes assigned to them<br>




   Working of the app<br>
    1.  Signed in the app based on teacher<br>
    2.  The app shows the present day class details. <br>
        This handles the case when an external teacher comes in she/he also gets to know what this class is all about<br>
        a) The opening page will show the date, teacher assigned, class name , no. of students, class timing<br>
        b) Getting "Date" - easy to get from the windows timing itself<br>
        c) Getting "Teacher Assigned" - Teacher will have to input the class name and based on the current timing, 
            day of the week the class details should come front.<br>
        d) Getting "Students List" - The input class name and timing will give the class id and the corresponding students listed.<br>
    3.  Teacher will press the attendance tab. The attendance page will open. It will show:<br>
        a) Names of the students listed under the class. On pressing present, it will create a new attendance-mark object id<br>
            taking in the class_id, student_id and date<br>
        b) It can show the graph attendance of the student for the class : by looking for class_id and student_id. 
            Limit the data to one month and show the graph.<br>




======================================================================================================================================================================
                                                                  UI DESIGN
======================================================================================================================================================================
