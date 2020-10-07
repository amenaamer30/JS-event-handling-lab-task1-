# JS-event-handling-lab-task1-


<!DOCTYPE html>
<html lang="en">
<head>
  <title>Bootstrap Example</title>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/css/bootstrap.min.css">
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
  <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/js/bootstrap.min.js"></script>
</head>
<body>

<div class="container-fluid">
  <div id="result"> </div>
  
  <div class="row">
    <div class="col-sm-8">
     <h3>List of Persons</h3>
     <br>
     <table class="table table-bordered data-table">
    <thead>
      <th>Name</th>
      <th>Gender</th>
      <th>Age</th>
      <th>City</th>
      <th width="200px">Action</th>
    </thead>
    <tbody>
    
    </tbody>
  </table>
    </div>
    <div class="col-sm-4">
    
    
    <h3>Add/Update Person Form</h3><br>
     <form style="border:2px solid black;padding:20px">
        
    <div class="form-group">
      <label>Name:</label>
      <input type="text" name="name"  required="">
    </div>
    
    <div class="form-group">
     <label>Gender:</label>
  <input type="radio" class="gender" name="gender" value="male" >
  <label for="male">Male</label>
  <input type="radio" class="gender" name="gender" value="female">
  <label for="female">Female</label><br><br>
    </div>
    
    
    <div class="form-group">
      <label>Age:</label>
      <input type="text" name="age"  required="">
    </div>
    
     <div class="form-group">
    <label>City:</label>
  <select id="city" name="city">
    <option value="Lahore">Lahore</option>
    <option value="Karachi">Karachi</option>
    <option value="Islamabad">Islamabad</option>
    <option value="Peshawar">Peshawar</option>
  </select>
  </div>
   
    <button type="submit" class="btn btn-info save-btn">Add</button>
    <button type="reset" class="btn btn-info btn-reset" onclick="reset();" >Reset</button>
    <button class="btn btn-info btn-update">Update</button>
    
  </form>
    </div>
    
  </div>
</div>
    
     <script type="text/javascript">
   var row_num;
    $("form").submit(function(e){
        e.preventDefault();
        var name = $("input[name='name']").val();
        var gender=$(".gender:checked").val();
        var age = $("input[name='age']").val();
        var city = $("#city").val();
     
     
        $(".data-table tbody").append("<tr data-name='"+name+"' data-gender='"+gender+"' data-age='"+age+"' data-city='"+city+"'><td>"+name+"</td><td>"+gender+"</td><td>"+age+"</td><td>"+city+"</td><td><button class='btn btn-info btn-xs btn-edit'>Edit</button><button class='btn btn-danger btn-xs btn-delete'>Delete</button></td></tr>");
    
        $("input[name='name']").val('');
        $("gender:checked='gender'").val('');
        $("input[name='age']").val('');
        $("#city").val('');
        
    });
   
    $("body").on("click", ".btn-delete", function(){
        $(this).parents("tr").remove();
    });
    
    
    function reset() {
    
    $("input[name='name']").val('');
        $("gender:checked='gender'").val('');
        $("input[name='age']").val('');
        $("#city").val('');
}
    
    $("body").on("click", ".btn-edit", function(){
        var name = $(this).parents("tr").attr('data-name');
        var gender = $(this).parents("tr").attr('data-gender');
        var age = $(this).parents("tr").attr('data-age');
        var city = $(this).parents("tr").attr('data-city');
    
    $("input[name='name']").val(name);
        $("input[name='age']").val(age);
        $("#city").val(city);
        
      
         row_num = parseInt( $(this).parents("tr").index() );

        $("#result").html( "Row_num =" + row_num );
   
        
       $(this).parents("tr").remove();
       $(".save-btn").hide();
    });
    
   $("body").on("click", ".btn-update", function(){
    var name = $(this).parents("tr").find("input[name='edit_name']").val();
        var gender = $(this).parents("tr").find("input[name='edit_gender']").val();    
        var age = $(this).parents("tr").find("input[name='edit_age']").val();
        var city = $(this).parents("tr").find("input[name='edit_city']").val();
    
        $(this).parents("tr").find("td:eq(0)").text(name);
        $(this).parents("tr").find("td:eq(1)").text(gender);
        $(this).parents("tr").find("td:eq(2)").text(age);
        $(this).parents("tr").find("td:eq(3)").text(city);
     
        $(this).parents("tr").attr('data-name', name);
        $(this).parents("tr").attr('data-gender', gender);
        $(this).parents("tr").attr('data-age', age);
        $(this).parents("tr").attr('data-city', city); 
        
         $(".save-btn").show();
    });
    
</script>
     
</body>
</html>
