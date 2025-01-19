Task on OBJECT ORIENTED ANALYSIS AND DESIGN

TASK 1: Creating UML Diagram and Implementing Classes
  a. Title: SCHOOL MANAGEMENT SYSTEM
      Description: This system enables enrollment of students, assigning of lecturers and assigning of courses.
 
  b. Creating a class diagram
      Student
      ATTRIBUTES: name. studentId, enrolledCourses, emailAddress
      METHODS: enrolledCourse, dropCourse

      Lecturer
      ATTRIBUTES: name, lecturerId, assignedCourses, emailAddress
      METHODS: assignCourse, removCourse

      Course
      ATTRIBUTES: courseTitle, courseCode, assignedLecturer, studentList
      METHODS: addStudent, removeStudent

    c. Code Implentation
      Below is a JavaScript code that implements the class in my diagram. It contains class/static properties for each class and two methos for each class.
    
    https://replit.com/@olusirasheedat/Object-Oriented-Analysis-And-Design#index.js

    
    
    class Student {
  static totalStudents = 0;

  constructor(name, studentId, enrolledCourses = [], emailAddress) {
    
    this.name = name;
    this.studentId = studentId;
    this.enrolledCourses = enrolledCourses;
    this.emailAddress = emailAddress;
    Student.totalStudents++;
    
  }

 
  enrollCourse(course) {
   
    if (!this.enrolledCourses.includes(course)) {
      this.enrolledCourses.push(course);
      course.addStudent(this);
      console.log(`${this.name} has enrolled in ${course.courseTitle}`);
    } else {
      console.log(`${this.name} has already enrolled in ${course.courseTitle}`);
    }
  }

  droppedCourse(course) {
    
    const index = this.enrolledCourses.indexOf(course);
    if (index !== -1) {
      this.enrolledCourses.splice(index, 1);
      course.removeStudent(this);
      console.log(`${this.name} has dropped ${course.courseTitle}`);
    } else {
      console.log(`${this.name} is not enrolled in ${course.courseTitle}`);
    }
  }

  static getTotalSudents() {
   
    return Student.totalStudents;
  }
  
}


class Lecturer {
  
  static totalLecturers = 0;

  constructor(name, lectureId, assignedCourses = [], emailAddress) {
   
    this.name = name;
    this.lectureId = lectureId;
    this.assignedCourses = assignedCourses;
    this.emailAddress = emailAddress;
    Lecturer.totalLecturers++;
  }

  assignCourse(course) {
   
    if (!this.assignedCourses.includes(course)) {
      this.assignedCourses.push(course);
      course.addLecturer = this;
      console.log(
        `${this.name} has been assigned to lecture ${course.courseTitle}`,
      );
    } else {
      console.log(
        `${this.name} has already been assigned to lecture ${course.courseTitle}`,
      );
    }
  }

  removeCourse(course) {
  
    const index = this.assignedCourses.indexOf(course);
    if (index !== -1) {
      this.assignedCourses.splice(index, 1);
      course.assignedLecturer = null;
      console.log(
        `${this.name} has been removed from lecturing ${course.courseTitle}`,
      );
    } else {
      console.log(
        `${this.name} is not assigned to lecture ${course.courseTitle}`,
      );
    }
  }

  static getTotalLecturers() {
   
    return Lecturer.totalLecturers;
  }
  
}


class Course {
 
  static totalCourses = 0;

  constructor(courseTitle, courseCode, assignLecturer, studentList) {
    
    this.courseTitle = courseTitle;
    this.courseCode = courseCode;
    this.assignLecturer = null;
    this.studentList = [];
    Course.totalCourses++;
  }

  addStudent(student) {
   
    if (!this.studentList.includes(student)) {
      this.studentList.push(student);
      console.log(`${student.name} has been added to the ${this.courseTitle}`);
    } else {
      console.log(`${student.name} is already enrolled in ${this.courseTitle}`);
    }
  }

  removeStudent(student) {
   
    const index = this.studentList.indexOf(student);
    if (index !== -1) {
      this.studentList.splice(index, 1);
      console.log(
        `${student.name} has been removed from this ${this.courseTitle}`,
      );
    } else {
      console.log(
        `${student.name} is not enrolled in this ${this.courseTitle}`,
      );
    }
  }
  static getTotalCourses() {
   
    return Course.totalCourses;
  }
  
}

const student1 = new Student(
  "Rasheedat Olusi",
  "FE501",
  [],
  "olusirasheedat@gmail.com",
);

const student2 = new Student(
  "Morayo Adeyemi",
  "FE322",
  [],
  "adeyemimo@gmail.com",
);

const student3 = new Student(
  "Candy Krush",
  "FE419",
  [],
  "candykrush@gmail.com",
);


const lecturer1 = new Lecturer(
  "Eze Livinus",
  "LEC001",
  [],
  "ezelivinus@gmail.com",
);

const lecturer2 = new Lecturer(
  "Simply Kachi",
  "LEC122",
  [],
  "simplykachi@gmail.com",
);

const lecturer3 = new Lecturer(
  "Falcon Dayo",
  "LEC314",
  [],
  "falcondayo@gmail.com",
);

const course1 = new Course("Javascript", "JS221");

const course2 = new Course("OOP", "OOP101");

const course3 = new Course("Git", "GIT312");

lecturer1.assignCourse(course1);

lecturer2.assignCourse(course3);

lecturer3.assignCourse(course2);

student1.enrollCourse(course1);

student2.enrollCourse(course3);

student3.enrollCourse(course2);

student1.droppedCourse(course2);

student2.droppedCourse(course1);

student3.droppedCourse(course3);

console.log(Student.getTotalSudents());

console.log(Lecturer.getTotalLecturers());

console.log(Course.getTotalCourses());






