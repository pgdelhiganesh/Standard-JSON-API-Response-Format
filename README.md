# Standard-JSON-API-Response-Format
Standard JSON API Response Format

### The main response structure have 4 keys which are
1.   status (bool) = "true" for successful response, "false" incase of fail or error occured.
2.   status_code (string) = User defiened value for success/fail/error.
3.   message (string) = User defined text for success/fail/error.
4.   data (object) = Can be anything, BOOL / INT / STRING / DECIMAL / Jobject / Jarray....
5.   log (object) = Can be anything.
6.   error.code (string) = User defiened value for fail/error.
7.   error.message (string) = User defined text for fail/error.

    public class ApiResponse
    {
        public ApiResponse()
        {
            error = new ErrorResponse();
        }

        [Required, DefaultValue(false)]
        public bool status { get; set; }

        [DefaultValue(null), StringLength(10)]
        public string? status_code { get; set; }

        [DefaultValue(null)]
        public object? data { get; set; }

        [DefaultValue(null)]
        public string? message { get; set; }
        
        public ErrorResponse error { get; set; }
        
        [DefaultValue(null)]
        public object? log { get; set; }
    }

    public class ErrorResponse
    {
        [DefaultValue(null), StringLength(10)]
        public string? code { get; set; }

        public string? message { get; set; }
    }

### For Success Response
```
{
  "status" : true,
  "status_code" : "SUCCESS",
  "message" : "Record Created Successfully."
  "data" : null,
  "error":
  {
    "code": null,
    "message": null
  }
  "log" : null
}
```

### For Failure / Error Response
```
{
  "status" : false,
  "status_code" : "FAIL/ERROR",
  "message" : "Cannot Create Record."
  "data" : null,
  "error":
  {
    "code": "PM1001",
    "message": "Parameter Missing or Invalid."
  }
  "log" : null
}
```

### For Data Read Response
```
{
  "status" : true,
  "status_code" : "SUCCESS",
  "message" : null,
  "data" :
    "users" : [
            { "id" : 1, "name" : "ABC", "age" : 18 },
            { "id" : 2, "name" : "XYZ", "age" : 36 }
        ],
  "error":
  {
    "code": null,
    "message": null
  }
  "log" : null
}
```
