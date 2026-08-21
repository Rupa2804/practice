 SELECT DATABASE:

use schoolDB

INSERT STUDENTS DATA:

db.students.insertMany([
  {
    name: "Aarav",
    age: 21,
    department: "CSE",
    marks: 88,
    city: "Hyderabad",
    skills: ["Python", "SQL", "Java"],
    fees: {
      total: 60000,
      paid: 45000
    }
  },
  {
    name: "Meera",
    age: 22,
    department: "ECE",
    marks: 65,
    city: "Vijayawada",
    skills: ["Python", "C", "SQL"],
    fees: {
      total: 55000,
      paid: 30000
    }
  },
  {
    name: "Rahul",
    age: 23,
    department: "CSE",
    marks: 92,
    city: "Hyderabad",
    skills: ["Python", "Git", "SQL"],
    fees: {
      total: 65000,
      paid: 60000
    }
  },
  {
    name: "Sneha",
    age: 20,
    department: "ECE",
    marks: 78,
    city: "Chennai",
    skills: ["C", "Java", "SQL"],
    fees: {
      total: 58000,
      paid: 40000
    }
  },
  {
    name: "Kiran",
    age: 22,
    department: "CSE",
    marks: 55,
    city: "Warangal",
    skills: ["Python", "HTML", "CSS"],
    fees: {
      total: 60000,
      paid: 25000
    }
  },
  {
    name: "Priya",
    age: 21,
    department: "EEE",
    marks: 84,
    city: "Hyderabad",
    skills: ["Python", "MATLAB", "SQL"],
    fees: {
      total: 50000,
      paid: 35000
    }
  },
  {
    name: "Vikram",
    age: 24,
    department: "ECE",
    marks: 91,
    city: "Bangalore",
    skills: ["Python", "Java", "Git"],
    fees: {
      total: 55000,
      paid: 50000
    }
  },
  {
    name: "Ananya",
    age: 22,
    department: "CSE",
    marks: 73,
    city: "Hyderabad",
    skills: ["Python", "SQL", "Git"],
    fees: {
      total: 62000,
      paid: 42000
    }
  },
  {
    name: "Rohit",
    age: 20,
    department: "MECH",
    marks: 58,
    city: "Pune",
    skills: ["AutoCAD", "Python"],
    fees: {
      total: 48000,
      paid: 20000
    }
  },
  {
    name: "Divya",
    age: 23,
    department: "CSE",
    marks: 96,
    city: "Vizag",
    skills: ["Python", "SQL", "Java", "Git"],
    fees: {
      total: 65000,
      paid: 65000
    }
  },
  {
    name: "Arjun",
    age: 21,
    department: "ECE",
    marks: 67,
    city: "Hyderabad",
    skills: ["C", "Python", "Git"],
    fees: {
      total: 57000,
      paid: 32000
    }
  },
  {
    name: "Pooja",
    age: 22,
    department: "EEE",
    marks: 81,
    city: "Vijayawada",
    skills: ["Python", "SQL", "MATLAB"],
    fees: {
      total: 52000,
      paid: 38000
    }
  },
  {
    name: "Sanjay",
    age: 25,
    department: "CSE",
    marks: 49,
    city: "Chennai",
    skills: ["Java", "HTML", "CSS"],
    fees: {
      total: 60000,
      paid: 15000
    }
  },
  {
    name: "Lakshmi",
    age: 20,
    department: "ECE",
    marks: 87,
    city: "Vizag",
    skills: ["Python", "SQL", "Git"],
    fees: {
      total: 56000,
      paid: 50000
    }
  },
  {
    name: "Nikhil",
    age: 23,
    department: "CSE",
    marks: 76,
    city: "Bangalore",
    skills: ["Python", "Java", "SQL"],
    fees: {
      total: 63000,
      paid: 30000
    }
  }
])


INSERT DEPARTMENT VALUES:

db.departments.insertMany([
  {
    department: "CSE",
    HOD: "Dr. Kumar"
  },
  {
    department: "ECE",
    HOD: "Dr. Ramesh"
  },
  {
    department: "EEE",
    HOD: "Dr. Lakshmi"
  },
  {
    department: "MECH",
    HOD: "Dr. Prasad"
  }
])


db.students.find().pretty()

db.departments.find().pretty()



1. Insert a new student document

db.students.insertOne({
  name: "Rupa",
  age: 22,
  department: "CSE",
  marks: 85,
  city: "Hyderabad",
  skills: ["Python", "SQL"],
  fees: {
    total: 60000,
    paid: 40000
  }
})


 2. Display all students

db.students.find().pretty()


3. Display all students belonging to CSE

db.students.find({
  department: "CSE"
})

 4. Display all students whose city is Hyderabad

db.students.find({
  city: "Hyderabad"
})


5. Find the student named Aarav

db.students.find({
  name: "Aarav"
})

 6. Find students whose marks are greater than 80

db.students.find({
  marks: { $gt: 80 }
})

 7. Find students whose age is greater than 20 and less than 23

db.students.find({
  age: {
    $gt: 20,
    $lt: 23
  }
})

 8. Find students who belong to CSE and are from Hyderabad

db.students.find({
  department: "CSE",
  city: "Hyderabad"
})


 9. Display only student name and marks

db.students.find(
  {},
  {
    _id: 0,
    name: 1,
    marks: 1
  }
)


10. Find students belonging to either CSE or ECE

db.students.find({
  department: {
    $in: ["CSE", "ECE"]
  }
})



11. Find students who have Python as one of their skills

db.students.find({
  skills: "Python"
})


 12. Find students who have both Python and SQL

db.students.find({
  skills: {
    $all: ["Python", "SQL"]
  }
})


 13. Find students whose paid fees are less than 40000

db.students.find({
  "fees.paid": {
    $lt: 40000
  }
})


 14. Display top 3 students based on marks


db.students.find()
  .sort({
    marks: -1
  })
  .limit(3)


15. Display all unique cities

db.students.distinct("city")



 16. Update Meera's marks to 70

db.students.updateOne(
  {
    name: "Meera"
  },
  {
    $set: {
      marks: 70
    }
  }
)




db.students.find({
  name: "Meera"
})


17. Give 5 additional marks to all CSE students

db.students.updateMany(
  {
    department: "CSE"
  },
  {
    $inc: {
      marks: 5
    }
  }
)


 18. Add "git" to skills of all CSE students


db.students.updateMany(
  {
    department: "CSE"
  },
  {
    $addToSet: {
      skills: "git"
    }
  }
)

19. Increase fees.total by 2000 for all ECE students

db.students.updateMany(
  {
    department: "ECE"
  },
  {
    $inc: {
      "fees.total": 2000
    }
  }
)

 20. First verify students whose marks are below 60

db.students.find({
  marks: {
    $lt: 60
  }
})




db.students.deleteMany({
  marks: {
    $lt: 60
  }
})


db.students.find({
  marks: {
    $lt: 60
  }
})



21. Find average marks for each department

db.students.aggregate([
  {
    $group: {
      _id: "$department",
      averageMarks: {
        $avg: "$marks"
      }
    }
  }
])


22. Display each department with its number of students


db.students.aggregate([
  {
    $group: {
      _id: "$department",
      studentCount: {
        $sum: 1
      }
    }
  },
  {
    $sort: {
      studentCount: -1
    }
  }
])


23. Calculate pendingFees

db.students.aggregate([
  {
    $project: {
      _id: 0,
      name: 1,
      pendingFees: {
        $subtract: [
          "$fees.total",
          "$fees.paid"
        ]
      }
    }
  },
  {
    $sort: {
      pendingFees: -1
    }
  }
])


 24. Find top 3 most common skills

db.students.aggregate([
  {
    $unwind: "$skills"
  },
  {
    $group: {
      _id: "$skills",
      count: {
        $sum: 1
      }
    }
  },
  {
    $sort: {
      count: -1
    }
  },
  {
    $limit: 3
  }
])


 25. Join students with departments


db.students.aggregate([
  {
    $lookup: {
      from: "departments",
      localField: "department",
      foreignField: "department",
      as: "departmentDetails"
    }
  },
  {
    $unwind: "$departmentDetails"
  },
  {
    $project: {
      _id: 0,
      studentName: "$name",
      department: "$department",
      HOD: "$departmentDetails.HOD"
    }
  }
])

26.BONUS

db.students.aggregate([
  {
    $group: {
      _id: "$department",
      averageMarks: {
        $avg: "$marks"
      },
      highestMarks: {
        $max: "$marks"
      },
      studentCount: {
        $sum: 1
      }
    }
  },
  {
    $sort: {
      averageMarks: -1
    }
  },
  {
    $project: {
      _id: 0,
      department: "$_id",
      averageMarks: 1,
      highestMarks: 1,
      studentCount: 1
    }
  }
])

