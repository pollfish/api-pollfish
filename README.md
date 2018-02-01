# Sample project

This project aims to help the developer to get,
show and handle a survey given by Pollfish through Pollfish API.

Inside the code, there are some mandatory variables that should be filled by the developer.Below is the list of these variables:
* api_key : (string) the given api_key
* device_id : (string) the device_id
* debug : (boolean) true on test mode
* request_uuid : (string) the request uuid
* acceptableCoins: (number) the amount of acceptable coins, in order to decide if the developer will show or not the survey

Also, in this example a proxy is used in order to bypass the CORS problem. In a real world scenario, you SHOULD NOT use this.

You can find a description of the usage below.

* On page load, there is a button `Request a new survey`
* Clicking this button, a request is sent in order to get a survey
    - If the returned status is 204 ( no survey available), an info message will be displayed informing the user that there is no available survey.
    - If the returned status is 400 or 500, an error message will be displayed informing the user that something went wrong
    - If the returned status is 200, then a button will be shown to the user informing him that after the completion of the survey, he will win some coins. By clicking this button, the survey will be shown.
        1. By clicking the close button or the `No thanks` button the survey will close and an info message will be shown along with the button `Request a new survey`
        2. By clicking the `Start survey` button the survey, the user will start answering the survey.
        3. By clicking `No` in the first question, the user will be screened out. If no survey is found after that, an info message will be shown informing the user that he was not eligible for a survey.
        4. By clicking `Yes`, the user will continue on the survey and on successful completion a message will be shown.

The handling of the `Pollfish` survey events is done inside ``` handlePollfishsEvents ``` function.


The flow above describes a real world scenario that includes all the possible events that can happen during the lifetime of a Pollfish survey. You should replace any step or messaging in order to apply to your own project.
