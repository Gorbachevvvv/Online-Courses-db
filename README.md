# Online-Сourses-db
# Горбачев Александр Кириллович гр. 253504
# Онлайн курсы
# 1. Определение темы проекта
Тема проекта: Система управления образовательным процессом, где студенты, преподаватели и администраторы взаимодействуют в рамках курсов и заданий. Система позволяет управлять пользователями, ролями, курсами, заданиями, посещаемостью и оценками.
# 1.1 Основные цели проекта
Управление пользователями: регистрация, авторизация и распределение ролей.
Администрирование курсов: создание и управление курсами, заданиями и оценками.
Учет посещаемости: отслеживание посещаемости студентов на занятиях.
Управление оценками: выставление и хранение оценок за выполненные задания.
# 2. Определение функциональных требований
Основные функциональные требования:
Авторизация пользователя.
Система ролей: пользователь может быть студентом, преподавателем или администратором.
Управление пользователями (CRUD).
Управление курсами и заданиями (CRUD).
Управление посещаемостью студентов.
Управление оценками и комментариями преподавателей.
# 3. Определение сущностей базы данных
# 3.1 Сущности
1. User (Пользователь)
id: INTEGER, NOT NULL, PK
name: VARCHAR(100), NOT NULL
password: VARCHAR(100), NOT NULL
email: VARCHAR(100), NOT NULL
telephone_number: VARCHAR(100), NOT NULL
Связи:
Один пользователь может иметь несколько ролей (Role).
Пользователь может быть студентом, преподавателем или администратором.

2. Role (Роль)
id: INTEGER, NOT NULL, PK
user_id: INTEGER, NOT NULL, FK -> User
permission_id: INTEGER, NOT NULL, FK -> Permission
role_name: STRING, NOT NULL
permission: VARCHAR(100), NOT NULL

3.Permission (Разрешение)
id: INTEGER, NOT NULL, PK
is_super_user: BOOLEAN, NOT NULL
is_staff: BOOLEAN, NOT NULL

4.Admin (Администратор)
id: INTEGER, NOT NULL, PK
user_id: INTEGER, NOT NULL, FK -> User

5.Student (Студент)
id: INTEGER, NOT NULL, PK
user_id: INTEGER, NOT NULL, FK -> User
class_id: VARCHAR(100), NOT NULL, FK -> Class

6.Teacher (Преподаватель)
id: INTEGER, NOT NULL, PK
user_id: INTEGER, NOT NULL, FK -> User
specialization: VARCHAR(100), NOT NULL

7.Class (Класс)
id: INTEGER, NOT NULL, PK
field: STRING, NOT NULL
student_id: INTEGER, NOT NULL, FK -> Student
teacher_id: INTEGER, NOT NULL, FK -> Teacher
time: INTEGER, NOT NULL

8.Attendance (Посещаемость)
id: INTEGER, NOT NULL, PK
class_id: STRING, NOT NULL, FK -> Class
date: DATE, NOT NULL
status: VARCHAR(10), NOT NULL

9.Task (Задание)
id: INTEGER, NOT NULL, PK
class_id: STRING, NOT NULL, FK -> Class
status: STRING, NOT NULL
description: STRING, NOT NULL

10.Grade (Оценка)
grade_id: INTEGER, NOT NULL, PK
student_id: INTEGER, NOT NULL, FK -> Student
task_id: INTEGER, NOT NULL, FK -> Task
grade: DECIMAL(5, 2), NOT NULL
comments: TEXT
# 3.2 Описание сущностей
User (Пользователь): Содержит основную информацию о пользователях системы, включая их идентификационные данные, пароль, электронную почту и номер телефона.
Role (Роль): Определяет, какую роль (например, студент, преподаватель или администратор) выполняет пользователь в системе.
Permission (Разрешение): Устанавливает, какие действия разрешено выполнять пользователю с определенной ролью.
Admin (Администратор): Пользователь, обладающий привилегиями администратора, с возможностью управления другими пользователями и их ролями.
Student (Студент): Пользователь, участвующий в учебных курсах.
Teacher (Преподаватель): Пользователь, ответственный за ведение курсов и выставление оценок.
Class (Класс): Учебная группа, объединяющая студентов и преподавателей для прохождения учебного курса.
Attendance (Посещаемость): Таблица, фиксирующая присутствие студентов на занятиях.
Task (Задание): Учебные задания, которые получают студенты в рамках курсов.
Grade (Оценка): Оценки, которые студенты получают за выполнение заданий, вместе с комментариями преподавателей.
