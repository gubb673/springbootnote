
# dao

```java
package cn.itcast.springboot.dao;

import cn.itcast.springboot.entity.Student;

import java.util.Collection;

public interface StudentDAO {

    //获取所有的student
    Collection<Student> getAllStudents();

    /**
     * @param id
     * 根据id获取学生
     *
     * @return Student
     * 返回对应的学生对象
     **/
    Student getStudentById(Long id);


    /**
     * @param student
     * 传入新的student数据
     *
     * @return Collection<Student>
     * 修改成功后返回所有的student
     * */
    Collection<Student> updateStudentById(Student student);


    /**
     * @param student
     * 传入新的student数据
     *
     * @return Collection<Student>
     * 新增成功后返回所有的student
     * */
    Collection<Student> addStudentById(Student student);


    /**
     * @param id
     * 传入要删除的student的id
     *
     * @return Collection<Student>
     * 删除成功后返回所有的student
     * */
    Collection<Student> deleteStudentById(Long id);

}
```

# dao impl

```java
package cn.itcast.springboot.dao;

import cn.itcast.springboot.entity.Student;
import org.springframework.stereotype.Repository;

import java.util.Collection;
import java.util.Date;
import java.util.HashMap;
import java.util.Map;

@Repository("fakeDAO")
public class StudentDAOImpl implements StudentDAO {

    Map<Long,Student> studentMap = new HashMap<Long,Student>(){{
        put(10086L,new Student(10086L,"刘德华",50,new Date()));
        put(10087L,new Student(10087L,"张学友",51,new Date()));
        put(10088L,new Student(10088L,"霍建华",52,new Date()));
        put(10089L,new Student(10089L,"郭富城",53,new Date()));
        put(10090L,new Student(10090L,"陈冠希",54,new Date()));
    }};

    @Override
    public Collection<Student> getAllStudents() {
        return studentMap.values();
    }

    @Override
    public Student getStudentById(Long id) {
        return studentMap.get(id);
    }

    @Override
    public Collection<Student> updateStudentById(Student student) {
        studentMap.put(student.getId(),student);
        return studentMap.values();
    }

    @Override
    public Collection<Student> addStudentById(Student student) {
        studentMap.put(student.getId(),student);
        return studentMap.values();
    }

    @Override
    public Collection<Student> deleteStudentById(Long id) {
        studentMap.remove(id);
        return studentMap.values();
    }
}

```