# python07

## Try this

students.csv 파일에 10명의 학생정보\(이름,성별,나이,성적\) 있습니다.  
\(홍길동,남,23,80\)

1. 이 파일을 읽어\(open\) 성적순으로 출력 \(sort or sorted\)
2. 이름은 홍\*\* 형태로, 성적은 학점으로 표현 \( \_\_str\_\_ \)
3. 총점과 평균을 구하시오. \(reduce\)
4. 평균 이상인 학생 이름, 성적 출력 \(filter\)

{% code-tabs %}
{% code-tabs-item title="student.py" %}
```python
from functools import reduce

g_grades = ['A','B','C','D','F']
g_grades.reverse()

class Student:
    grade = ''
    def __init__(self, line):
        name, gender, age, score = line.strip().split(',')
        self.name = name
        self.gender = gender
        self.age = age
        self.score = int(score)

    # toString
    def __str__(self):
        return "{}**\t{}\t{}\t{}".format(self.name[0], self.gender, self.age, self.grade)

    def make_grade(self):
        if self.score == 100:
            self.grade = 'A+'
        else: 
            self.grade = g_grades[self.score // 10 - 5]

#print(g_grades)

students = []

with open("students.csv","r",encoding="utf8") as file:
    for i, line in enumerate(file):
        if i == 0: continue
        # print(line.strip().split(','))
        students.append(Student(line))

students.sort(key=lambda stu: stu.score, reverse=True)
m = map(lambda stu: stu.make_grade(), students)
list(m)

# A if type(x) == int else B #Python
# type(x) == int ? A : B #Java
# if type(x) == int: 
#     A
# else: 
#     B

def sumfn(x,y):
    if type(x) == int:
        return x + y.score
    else:
        return x.score + y.score

# total = reduce(lambda x,y: (x if type(x) == int else x.score) + y.score, students)
total = reduce(sumfn, students)
avg = total / len(students)
print("총계, 평균 >>> ", total, avg)

print("이름\t성별\t나이\t학점")
print("----\t----\t----\t----")
for s in students:
    print(s)

print("------------------------")
for s in students:
    if s.score > avg:
        print(s.name, s.score)

```
{% endcode-tabs-item %}
{% endcode-tabs %}

