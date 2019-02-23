# lab2
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>

<script>
    var VehicleName="toyota";

    function printvehiclenameOuter()
    {
        console.log(this.VehicleName);
    }

    printvehiclenameOuter();
    console.log(this);

    var Vehicle ={
        VehicleName:"Nisan",
       // printvehicleNameInner : printvehiclenameOuter

        printvehicleNameInner :function()
        {
            return function() {
                console.log(this.VehicleName)
            }
        }
    };

    var execute=Vehicle.printvehicleNameInner()//.bind(Vehicle);
    execute.call(Vehicle);
//execute();
    //execute.bind(Vehicle);
    //Vehicle.printvehicleNameInner();


    function Car(){

    }

</script>

</body>
</html>

//question 4

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>

<script>
    function Vehicle(type)
    {
        Vehicle.VehicleCount++;
        this.type =type;
    }

    Vehicle.prototype.drive=function()
    {
        console.log("Vehicle i driving");
    }

   var vehicle=new Vehicle("toyota");
   // console.log(vehicle)
    // create static variable
    Vehicle.VehicleCount=0;

    function Car()
    {
        Vehicle.call();


    }

 //inherit
    Car.prototype=Object.create(Vehicle.prototype);

       //stop constructor change
        Car.constructor=Car;

        Car.prototype.BallenceWheel=function()
    {
        console.log("wheels are balanced");
    }

    var car=new Car();
    car.drive();
    car.BallenceWheel();
    console.log(car.type,Vehicle.VehicleCount);






</script>
</body>
</html>
