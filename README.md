Config file in Angular2

	In .net there is specific file to load settings before application startup. For Angular2 we must create “json” file for this purpose. 

In this document, I will show you how to read the data in Angular 2 before application startup.  

Overall flow 
1)	It will read ‘env.json’ file. This will indicate current environment either ‘production’ or ‘development’.
2)	Based on data in ‘env.json’, If it is ‘production’ then it will read ‘config.production.json’ and if it is ‘development’ then it will read from ‘config.development.json’.

Directory Structure (In our case)
 	                                                 












App.module.ts

 



1)	This makes sure that AppConfig which we are going to implement further is available for Angular 2
2)	APP_INITIALIZER execute config.load() method before application start.
3)	‘multi:true’ : Applcation can have more than one line of APP_INITLIZER.











App.config.ts

You can choose a name of your choice. This will read the ‘env.json’ files and data from both files will retrieve later.
(Note: Http library is used to read json files)


 
1)	Promise: Web APIs returns promises for async operations like fetch().
2)	http.get(): This accessing the data straightforward.
3)	map(): It is not the function it is operator. For this we must import 'rxjs/add/operator/map'
4)	resolve(): Interface that class can implemented to be a data provider.
5)	Subscribe(): This function actually executes the observable. 



  
1)	Switch case for the choosing environment as per the value in ‘env.json’.
2)	If block for successful execution of switch block (Not execution of default case) and maps data from development/production.json.
3)	Else block for default execution of switch case. This is for exception handling.



env.json
 

config.production.json
 

config.development.json
 


App.component.ts
 



Second.component.ts
  

1)	Imported class AppConfig.
2)	Created constructor and private variable.
3)	Initialization of the variables 
Object getConfig(String key){}
	The function is written in such a way that you can pass key as an argument to it which returns value associated with that key from ‘config.production.json / config.production.json’ as per environment in ‘env.json’ file.
4)	HTML code.

