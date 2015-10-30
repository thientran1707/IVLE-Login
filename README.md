"Login-Page-Free" IVLE Login for developers
======
##Background Problem
Many of SoC fellows enjoys hacking with [IVLE](https://ivle.nus.edu.sg/), as this is the platform that every NUS student must be using everyday. After logging into the system, you will be able to access the useful resources provided on IVLE, such as workbins and forums.

The IVLE team generously provides the API reference as well as some example codes so that every NUS student who likes to do something with IVLE can start coding immediately.

As IVLE uses an OAuth-like authentication, you are forced to be redirected to an ***infamous*** login page in all sample codes provided, which immediately makes your well-designed lovely application an ugly and inconsistent one. 

![Sample screenshot](http://i.imgur.com/fgQl9t5.png)

However, in all sample codes, you cannot escape the login step as you can only acquire the necessary **token** in the callback url after you have successfully logged into the system. Such mechanism is quite inconvenient for mobile apps because you need to open things like a webview for the login process.

This repo will help you to eliminate such login page (it's quite simple) so you can safely create your own login UI and make your application consistent from login to logout.

##What you need in this tutorial
Get your [IVLE API Key](http://ivle.nus.edu.sg/LAPI/default.aspx) if you have not done so.

A HTTP client you can play with.

and the [IVLE API reference](https://wiki.nus.edu.sg/display/ivlelapi/LAPI+Reference) so you can start hacking.

##TL;DR
Get your API key, and use this url for login.
```
https://ivle.nus.edu.sg/api/login/?apikey={Your API key}&url=
```
Submit a POST request to the above url with header ```Content-Type: application/x-www-form-urlencoded```, and the following data:

| Key  | Value |
| ------------- | ------------- |
| userid                | *Your NUSNET id*  |
| password              | *Your password*  |
| __VIEWSTATE           | /wEPDwULLTEzODMyMDQxNjEPFgIeE1ZhbGlkYXRlUmVxdWVzdE1vZGUCARYCAgEPZBYEAgEPD2QWAh4Gb25ibHVyBQ91c2VySWRUb1VwcGVyKClkAgkPD2QWBB4Lb25tb3VzZW92ZXIFNWRvY3VtZW50LmdldEVsZW1lbnRCeUlkKCdsb2dpbmltZzEnKS5zcmM9b2ZmaW1nLnNyYzE7Hgpvbm1vdXNlb3V0BTRkb2N1bWVudC5nZXRFbGVtZW50QnlJZCgnbG9naW5pbWcxJykuc3JjPW9uaW1nLnNyYzE7ZBgBBR5fX0NvbnRyb2xzUmVxdWlyZVBvc3RCYWNrS2V5X18WAQUJbG9naW5pbWcxYTg4Q/LO3lNCB13iJpTeINmF1JQmGv61ni1TVgDIOII= |
| __VIEWSTATEGENERATOR  | B0AF59B8  |

*What is viewstate? It's just a special value used in ASP.NET Web Forms. This step actually simulates what is going on if you click the login button in the login page. [Read more](http://www.w3schools.com/aspnet/aspnet_viewstate.asp)

If everything goes well, you will receive the token as response. No callback url is needed at all. 

Below is a sample screenshot using Postman.

![Sample screenshot](http://i.imgur.com/hzuANIk.png)

Now just store the token and use it in your request.

##What's next?
As every token has its expire time. You should [validate](https://wiki.nus.edu.sg/display/ivlelapi/Login) the token when necessary. 

##Disclaim
The method stated above can be easily found if you understand a little HTTP and with Chrome's developer tool. 

At the time of writing this repo, this method is working perfectly. It may work for a long time but **no guarantee is made**.

The repo should be using for learning and developing purpose only.

This repo is not a good practice in general XD.
