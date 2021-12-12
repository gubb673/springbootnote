# service
```java
package cn.itcast.springboot.service;

import cn.itcast.springboot.entity.Student;

import java.util.Collection;

public interface StudentService {

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

# service impl
```java
package cn.itcast.springboot.service;

import cn.itcast.springboot.dao.StudentDAO;
import cn.itcast.springboot.entity.Student;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

import java.util.Collection;

@Service
public class StudentServiceImpl implements StudentService {

    @Autowired
    private StudentDAO studentDAO;

    @Override
    public Collection<Student> getAllStudents() {
        return studentDAO.getAllStudents();
    }

    @Override
    public Student getStudentById(Long id) {
        return studentDAO.getStudentById(id);
    }

    @Override
    public Collection<Student> updateStudentById(Student student) {
        return studentDAO.updateStudentById(student);
    }

    @Override
    public Collection<Student> addStudentById(Student student) {
        return studentDAO.addStudentById(student);
    }

    @Override
    public Collection<Student> deleteStudentById(Long id) {
        return studentDAO.deleteStudentById(id);
    }
}
```