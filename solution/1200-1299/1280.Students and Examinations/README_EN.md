# [1280. Students and Examinations](https://leetcode.com/problems/students-and-examinations)

[中文文档](/solution/1200-1299/1280.Students%20and%20Examinations/README.md)

## Description

<p>Table: <code>Students</code></p>

<pre>
+---------------+---------+
| Column Name   | Type    |
+---------------+---------+
| student_id    | int     |
| student_name  | varchar |
+---------------+---------+
In SQL, student_id is the primary key for this table.
Each row of this table contains the ID and the name of one student in the school.
</pre>

<p>&nbsp;</p>

<p>Table: <code>Subjects</code></p>

<pre>
+--------------+---------+
| Column Name  | Type    |
+--------------+---------+
| subject_name | varchar |
+--------------+---------+
In SQL, subject_name is the primary key for this table.
Each row of this table contains the name of one subject in the school.
</pre>

<p>&nbsp;</p>

<p>Table: <code>Examinations</code></p>

<pre>
+--------------+---------+
| Column Name  | Type    |
+--------------+---------+
| student_id   | int     |
| subject_name | varchar |
+--------------+---------+
This table may contain duplicates (In other words, there is no primary key for this table in SQL).
Each student from the Students table takes every course from the Subjects table.
Each row of this table indicates that a student with ID student_id attended the exam of subject_name.
</pre>

<p>&nbsp;</p>

<p>Find the number of times each student attended each exam.</p>

<p>Return the result table ordered by <code>student_id</code> and <code>subject_name</code>.</p>

<p>The result format is in the following example.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> 
Students table:
+------------+--------------+
| student_id | student_name |
+------------+--------------+
| 1          | Alice        |
| 2          | Bob          |
| 13         | John         |
| 6          | Alex         |
+------------+--------------+
Subjects table:
+--------------+
| subject_name |
+--------------+
| Math         |
| Physics      |
| Programming  |
+--------------+
Examinations table:
+------------+--------------+
| student_id | subject_name |
+------------+--------------+
| 1          | Math         |
| 1          | Physics      |
| 1          | Programming  |
| 2          | Programming  |
| 1          | Physics      |
| 1          | Math         |
| 13         | Math         |
| 13         | Programming  |
| 13         | Physics      |
| 2          | Math         |
| 1          | Math         |
+------------+--------------+
<strong>Output:</strong> 
+------------+--------------+--------------+----------------+
| student_id | student_name | subject_name | attended_exams |
+------------+--------------+--------------+----------------+
| 1          | Alice        | Math         | 3              |
| 1          | Alice        | Physics      | 2              |
| 1          | Alice        | Programming  | 1              |
| 2          | Bob          | Math         | 1              |
| 2          | Bob          | Physics      | 0              |
| 2          | Bob          | Programming  | 1              |
| 6          | Alex         | Math         | 0              |
| 6          | Alex         | Physics      | 0              |
| 6          | Alex         | Programming  | 0              |
| 13         | John         | Math         | 1              |
| 13         | John         | Physics      | 1              |
| 13         | John         | Programming  | 1              |
+------------+--------------+--------------+----------------+
<strong>Explanation:</strong> 
The result table should contain all students and all subjects.
Alice attended the Math exam 3 times, the Physics exam 2 times, and the Programming exam 1 time.
Bob attended the Math exam 1 time, the Programming exam 1 time, and did not attend the Physics exam.
Alex did not attend any exams.
John attended the Math exam 1 time, the Physics exam 1 time, and the Programming exam 1 time.
</pre>

## Solutions

<!-- tabs:start -->

### **SQL**

```sql
# Write your MySQL query statement below
SELECT
    a.student_id,
    student_name,
    b.subject_name,
    count(c.subject_name) AS attended_exams
FROM
    Students AS a
    CROSS JOIN Subjects AS b
    LEFT JOIN Examinations AS c
        ON a.student_id = c.student_id AND b.subject_name = c.subject_name
GROUP BY a.student_id, b.subject_name
ORDER BY a.student_id, b.subject_name;
```

<!-- tabs:end -->
