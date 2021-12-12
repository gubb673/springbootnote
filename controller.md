# 1. Controller

import java packages

```java
package cn.itcast.springboot.controller;

import cn.itcast.springboot.entity.Student;
import cn.itcast.springboot.service.StudentService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.*;

import java.util.Collection;
```


## Restful api
```bash
POST http://localhost:8080/students
```

```java
@RequestMapping("students")
public class StudentController {
    ...
}
```

## @Autowired 
It allows Spring to resolve and inject collaborating beans into our bean.
```java
@Autowired
private StudentService studentService;
```

## Get请求
```java
@GetMapping
public Collection<Student> getAllStudents(){
    return studentService.getAllStudents();
}
```

## Post请求
```java
@PostMapping(value = "/add")
public Collection<Student> addStudentById(@RequestBody Student newStudent) {
    System.out.print(newStudent.toString() + '\n');
    return studentService.addStudentById(newStudent); 
}
```

## Path variable
```java
@DeleteMapping(value = "/{id}")
public Collection<Student> deleteStudentById(@PathVariable("id") Long id){
    return studentService.deleteStudentById(id);
}
```




```java
@RestController

@RequestMapping("students")
public class StudentController {
    @Autowired
    private StudentService studentService;

    @GetMapping
    public Collection<Student> getAllStudents(){
        return studentService.getAllStudents();
    }

    @PostMapping(value = "/add")
    public Collection<Student> addStudentById(@RequestBody Student newStudent) {
        System.out.print(newStudent.toString() + '\n');
        return studentService.addStudentById(newStudent); }

    @GetMapping(value = "/{id}")
    public Student getStudentById(@PathVariable("id") Long id){
        return studentService.getStudentById(id);
    }

    @DeleteMapping(value = "/{id}")
    public Collection<Student> deleteStudentById(@PathVariable("id") Long id){

        return studentService.deleteStudentById(id);
    }
}
```
