//Attendance Schema
//  The date will keep on incrementing and _id will change too
{
  "_id": ObjectId("..."), 
  "student_id": ObjectId("..."), // ID of the student attending the class
  "class_id": ObjectId("..."), // ID of the class being attended
  "date": ISODate("..."), // Date of the attendance record
  "status": "present" // Attendance status (present/absent/tardy/etc.)
}

//Student Schema
//1. We will have the student-centric entries
//2. Therefor we will have classes allotted to student and not the other way around
//3. This also takes care of the culture as followed in colleges

{
  "_id": ObjectId("..."), // Unique ID for the student
  "name": "John Doe", // Full name of the student
  "email": "john.doe@example.com", // Email address of the student
  "dob": ISODate("2005-01-01"), // Date of birth of the student
  "gender": "male", // Gender of the student
  "phone": "+1 555-123-4567", // Phone number of the student
  "address": {
    "street": "123 Main St.",
    "city": "Any-town",
    "state": "CA",
    "zip": "12345"
  }, // Address of the student
  "enrollment_date": ISODate("2020-09-01"), // Date when the student enrolled in the school
}


//Class Schema
//This schema is where both the teachers and students meet

{
  "_id": ObjectId("..."), // Unique ID for the class
  "name": "Chemistry 101", // Name of the class
  "teacher_id": ObjectId("..."), // ID of the teacher for the class
  "start_time": ISODate("2023-05-01T09:00:00Z"), // Start time of the class
  "end_time": ISODate("2023-05-01T10:30:00Z"), // End time of the class
  "students": [
    {
      "student_id": ObjectId("..."), // ID of a student in the class
      "enrollment_date": ISODate("2020-09-01") // Date when the student enrolled in the class
    },
    {
      "student_id": ObjectId("..."),
      "enrollment_date": ISODate("2020-09-01")
    },
    // ... additional students in the class ...
  ]
}

/*
    Input fetched to the software by the school
    1. List of students enrolled with their class room name and their personal details
    2. An updated time table 
    3. List of teachers and classes assigned to them

*/



/*  Working of the app
    1.  Signed in the app based on teacher
    2.  The app shows the present day class details. 
        This handles the case when an external teacher comes in she/he also gets to know what this class is all about
        a) The opening page will show the date, teacher assigned, class name , no. of students, class timing
        b) Getting "Date" - easy to get from the windows timing itself
        c) Getting "Teacher Assigned" - Teacher will have to input the class name and based on the current timing, 
            day of the week the class details should come front.
        d) Getting "Students List" - The input class name and timing will give the class id and the corresponding students listed.

    3.  Teacher will press the attendance tab. The attendance page will open. It will show:
        a) Names of the students listed under the class. On pressing present, it will create a new attendance-mark object id
            taking in the class_id, student_id and date
        b) It can show the graph attendance of the student for the class : by looking for class_id and student_id. 
            Limit the data to one month and show the graph.


*/  
