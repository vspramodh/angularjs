# angularjs

how to do curd operations in angular js with api serivces and routes

<html ng-app="crudApp" ng-controller="crudController">

<head>
    <h1>Angular js curd operations</h1>
    <scripts img="srcipts/angular.min.js"></scripts>

    <!-- Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet"
        integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">

    <!-- <style>
        table {
            width: 100%;
        }

        table,
        th,
        td {
            border: solid 1px #DDD;
            border-collapse: collapse;
            padding: 2px 3px;
            text-align: center;
        }

        input[type='button'] {
            cursor: pointer;
            border: none;
            color: #FFF;
        }

        input[type='text'],
        select {
            text-align: center;
            border: solid 1px #CCC;
            width: auto;
            padding: 2px 3px;
        }
    </style> -->

</head>

<body>
    <div ng-app="crudApp">

        <section ng-controller="crudController"></section>
        <table class="table table-striped">
            <thead>
                <tr>

                    <th>S.No</th>
                    <th>User Name</th>
                    <th>Password</th>
                    <th>Role Id</th>
                    <th>V Name</th>
                    <th>Employee ID</th>
                    <th>Token</th>
                    <th>Status</th>

                </tr>

                <tr>

                    <th><input type="text" class="form-control" placeholder="UserId" ng-model="UserId"></th>
                    <th><input type="text" class="form-control" placeholder="UserName" ng-model="UserName"></th>
                    <th><input type="text" class="form-control" placeholder="Password" ng-model="Password"></th>
                    <th><input type="text" class="form-control" placeholder="RoleId" ng-model="RoleId"></th>
                    <th><input type="text" class="form-control" placeholder="Status" ng-model="Status"></th>
                    <th><input type="text" class="form-control" placeholder="VId" ng-model="VId"></th>
                    <th><input type="text" class="form-control" placeholder="EmpId" ng-model="EmpId"></th>
                    <th><input type="text" class="form-control" placeholder="token" ng-model="token"></th>
                    <input type="hidden" ng-model="newStaff.UserId" />
                    <input type="button" value="Save" ng-click="saveRecord()" class="btn btn-primary" />
                </tr>
            </thead>
            <tbody>
                <tr ng-repeat="data in Staff" data-ng-click="BindSelectedData(data)">
                    <td>{{ data.UserId }}</td>
                    <td>{{ data.UserName }}</td>
                    <td>{{ data.Password }}</td>
                    <td>{{ data.RoleId }}</td>
                    <td>{{ data.Status }}</td>
                    <td>{{ data.VId }}</td>
                    <td>{{ data.EmpId }}</td>
                    <td>{{ data.token }}</td>
                    <td>
                        <a href="#" ng-click="edit(Staff.UserId)">edit</a> |
                        <a href="#" ng-click="delete(Staff.UserId)">delete</a>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>

    <!-- <script type="text/javascript" src="main.js"></script> -->
</body>

</html>
<script>


    // var app = angular.module('crudApp', []);
    // app.controller('crudController', function ($scope, $http) {
    //     $http.get("Staff")
    //         .then(function (response) { $scope.names = response.data.records; });
    // });


    // var app = angular.module("crudApp", []);
    // app.controller('crudController', function ($scope) {
    $scope.saveRecord = function () {

        if ($scope.newStaff.UserId == null) {

            $scope.newStaff.UserId = UserId++;

            $scope.Staff.push($scope.newStaff);

        } else {

            for (UserId in $scope.Staff) {

                if ($scope.Staff[UserId].UserId == $scope.newStaff.UserId) {

                    $scope.Staff[UserId] = $scope.newStaff;

                }

            }

        }
        $scope.newStaff = {};
    }


    // });


    $scope.delete = function (UserId) {

        for (UserId in $scope.Staff) {

            if ($scope.Staff[UserId].UserId == UserId) {

                $scope.Staff.splice(UserId, 1);

                $scope.newStaff = {};

            }

        }

    }

    $scope.edit = function (UserId) {

        for (UserId in $scope.Staff) {

            if ($scope.Staff[UserId].UserId == UserId) {

                $scope.newStaff = angular.copy($scope.Staff[UserId]);

            }

        }

    }
</script>
