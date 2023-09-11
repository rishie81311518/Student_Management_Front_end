<template>
  <div class="container">
    <div class="card">
      <div class="card-header">
        <h4>
          Students
          <RouterLink to="/student/create" class="btn btn-primary float-end">
            Add Student
          </RouterLink>
        </h4>
      </div>

      <div class="card-body">
        <table class="table table-bordered">
          <thead>
            <tr>
              <th>Name</th>
              <th>Student ID</th>
              <th>Father Name</th>
              <th>Marks</th>
              <th>Actions</th>
            </tr>
          </thead>
          <tbody v-if="this.students.length > 0">
            <tr v-for="(student, index) in this.students" :key="index">
              <td>{{ student.student_name }}</td>
              <td>{{ student.student_id }}</td>
              <td>{{ student.student_father_name }}</td>
              <td>{{ student.student_marks }}</td>

              <td>
                <RouterLink to="#" class="btn btn-success float-end m-2">
                  Edit
                </RouterLink>
                <button type="button" class="btn btn-danger float-end m-2">
                  Delete
                </button>
              </td>
            </tr>
          </tbody>
          <tbody v-else>
            <tr>
              <td colspan="6">Loading ...</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "students",
  data() {
    return {
      students: [],
    };
  },
  mounted() {
    this.getStudents();
  },
  methods: {
    async getStudents() {
      const data = await fetch(
        "http://localhost:3002/api/products/allProducts",
        {
          method: "GET",
        }
      );
      const jsonData = await data.json();
      this.students = jsonData;
    },
  },
};
</script>
