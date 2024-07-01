function validateform() {
  var name = document.getElementById("name").value;
  var age = document.getElementById("age").value;
  var Address = document.getElementById("Address").value;
  var email = document.getElementById("email").value;

  if (name === "") {
    alert("Name is required");
    return false;
  }

  if (age === "") {
    alert("Age is required");
    return false;
  } else if (age < 0) {
    alert("Age must be a positive number");
    return false;
  }

  if (Address === "") {
    alert("Address is required");
    return false;
  }

  if (email === "") {
    alert("Email is required");
    return false;
  } else if (!email.includes("@")) {
    alert("Invalid email address");
    return false;
  }

  return true;
}

function showData() {
  var peopleList;
  if (localStorage.getItem("peopleList") === null) {
    peopleList = [];
  } else {
    peopleList = JSON.parse(localStorage.getItem("peopleList"));
  }

  var html = "";
  peopleList.forEach(function (element, index) {
    html += "<tr>";
    html += "<td>" + element.name + "</td>";
    html += "<td>" + element.age + "</td>";
    html += "<td>" + element.Address + "</td>";
    html += "<td>" + element.email + "</td>";
    html +=
      '<td><button onclick="deleteData(' +
      index +
      ')" class="btn btn-danger">Delete</button><button onclick="editData(' +
      index +
      ')" class="btn btn-warning m-2">Edit</button></td>';
    html += "</tr>";
  });

  document.querySelector("#crudTable tbody").innerHTML = html;
}

document.onload = showData();

function AddData() {
  if (validateform() === true) {
    var name = document.getElementById("name").value;
    var age = document.getElementById("age").value;
    var Address = document.getElementById("Address").value;
    var email = document.getElementById("email").value;

    var peopleList;
    if (localStorage.getItem("peopleList") === null) {
      peopleList = [];
    } else {
      peopleList = JSON.parse(localStorage.getItem("peopleList"));
    }

    peopleList.push({
      name: name,
      age: age,
      Address: Address,
      email: email,
    });

    localStorage.setItem("peopleList", JSON.stringify(peopleList));
    showData();

    document.getElementById("name").value = "";
    document.getElementById("age").value = "";
    document.getElementById("Address").value = "";
    document.getElementById("email").value = "";
  }
}

function deleteData(index) {
  var peopleList;
  if (localStorage.getItem("peopleList") === null) {
    peopleList = [];
  } else {
    peopleList = JSON.parse(localStorage.getItem("peopleList"));
  }

  peopleList.splice(index, 1);
  localStorage.setItem("peopleList", JSON.stringify(peopleList));
  showData();
}

function editData(index) {
  document.getElementById("Submit").style.display = "none";
  document.getElementById("Update").style.display = "block";

  var peopleList;
  if (localStorage.getItem("peopleList") === null) {
    peopleList = [];
  } else {
    peopleList = JSON.parse(localStorage.getItem("peopleList"));
  }

  document.getElementById("name").value = peopleList[index].name;
  document.getElementById("age").value = peopleList[index].age;
  document.getElementById("Address").value = peopleList[index].Address;
  document.getElementById("email").value = peopleList[index].email;

  document.getElementById("Update").onclick = function () {
    if (validateform() === true) {
      peopleList[index].name = document.getElementById("name").value;
      peopleList[index].age = document.getElementById("age").value;
      peopleList[index].Address = document.getElementById("Address").value;
      peopleList[index].email = document.getElementById("email").value;

      localStorage.setItem("peopleList", JSON.stringify(peopleList));
      showData();

      document.getElementById("name").value = "";
      document.getElementById("age").value = "";
      document.getElementById("Address").value = "";
      document.getElementById("email").value = "";

      document.getElementById("Submit").style.display = "block";
      document.getElementById("Update").style.display = "none";
    }
  };
}
