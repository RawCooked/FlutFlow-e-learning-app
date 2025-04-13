
# 📘 E-Learning App – FlutterFlow Project

A modern, role-based e-learning application built with FlutterFlow. The platform supports interactive courses, quizzes, and AI-assisted learning, tailored for **students**, **professors**, and **admins**.

---

## 🚀 Features

- 🔐 **Authentication** with role selection: Student, Professor, Admin  
- 📚 **Course Management** with videos, text lessons, and AI Teacher support  
- 📝 **Quiz System**: QCM (multiple choice) & text-based questions  
- 📈 **Student Progress Tracking** with GPA and course-specific stats  
- 👨‍🏫 **Professor Tools** for course and quiz creation  
- 🛠️ **Admin Panel** for managing users and monitoring activity

---

## 🗂️ Database Schema

### 🔸 `User`
Stores common user data and role-specific extensions.

```plaintext
User (
    id,
    name,
    email,
    password,
    role: ['student', 'professor', 'admin'],
    created_at,

    student {
        GPA,
        Progression [ 
            {
                course_id,
                completion_status,   // 'in_progress' | 'completed'
                score,
                last_activity
            }
        ],
        info_about_student {
            age,
            grade_level,
            school,
            interests[]
        }
    },

    professor {
        department,
        courses_created[] // list of course_ids
    },

    admin {
        permissions[],
        logs[]
    }
)
```

---

### 🔸 `Courses`
Holds all learning content types including video, text, and AI-based instruction.

```plaintext
Courses (
    id,
    title,
    description,
    content_type: ['video', 'text', 'ai_teacher'],
    content_url,
    created_by (professor_id),
    created_at
)
```

---

### 🔸 `Quiz`
Quiz questions associated with specific courses. Supports both QCM and text formats.

```plaintext
Quiz (
    id,
    course_id,
    question_type: ['QCM', 'text'],
    question,
    options[],           // only for QCM
    correct_answer,      // for both QCM and text
    created_by (professor_id)
)
```

---

## 🧭 User Flow Overview

### 👨‍🎓 Student
1. Sign up / log in  
2. Browse and view courses (video, text, AI Teacher)  
3. Take quizzes  
4. View results and track progress

### 👨‍🏫 Professor
1. Log in  
2. Create courses with multimedia content  
3. Add QCM/text-based quizzes  
4. View student performance

### 🛡️ Admin
1. Log in  
2. Manage users (students & professors)  
3. Moderate content and view logs

---

## 🛠️ Tech Stack

- **FlutterFlow** – UI & Logic Builder  
- **Firebase** – Auth, Firestore DB, Storage  
- **OpenAI API (optional)** – AI Teacher assistant  
- **Figma (optional)** – UI design prototyping

---

## 📌 Notes

- Designed for scalability with role-based access  
- Clean data model for easy Firebase integration  
- Optionally extendable with chat, notifications, badges, and more!
