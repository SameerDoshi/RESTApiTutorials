# What is REST?

##The Problem
Let's say you're writting an app that will track your customers.  You're going to need to:
1. View a customer
2. View a list of customers
3. Add a new customer
4. Edit a customer
5. Delete a customer

Standard stuff!  Your app will be hosted on the internet so you need to come up with URLs for your api.  Well now the world is your oyster.  You could do all kinds fo things- here're are a few optiosn:

1. View a customer - /api/view/{id} or /api/customer/{id}
2. View a list of customers /api/list or /api/search
3. Add a new customer /api/new/{id} or /api/add/{id}
4. Edit a customer /api/edit/{id}  OR /api/modify/{id} 
5. Delete a customer /api/delete/{id}

Well this could get hairy.  And you can imagine that every developer in the world who has a similar problem will come up with a differnt solution.  Let's not forget people who don't speak english as a primary language.  

Now let's say you have to interface with an app someone else wrote that tracks shipments to customers.  They have the same needs (view, list, add, edit, delete shipment) as you, but what did they chose to write thier api.   You could read thier documentation, but wouldn't it be easier if all of you just used the same notation? 

## Enter Rest
In 2000 [Roy Fielding](https://en.wikipedia.org/wiki/Roy_Fielding) wrote a doctoral thesis to address this problem.  The Representational State Transfer architecture stadnard is defined in his paper.  

In it's simplest form REST is a standard way to write APIs.

Instead of using naming conventions that can change with word choice REST uses HTTP methods:
HTTP METHODS 	

So let's take a look at our customer API again:
1. View a customer - HTTP GET: /api/customer?id={id} 
2. View a list of customers HTTP GET: /api/customer?{id list, page for paginated reults, orblank for all}
3. Add a new customer HTTP PUT /api/customer *put body contains customer name
4. Edit a customer HTTP POST /api/customer *post body contains {updated customer name, id}
5. Delete a customer HTTP DELETE /api/customer *delete body contains {id}

That's it! If the shipments API is REST then it's probably the same format, no need to read docs (which is good because you are a very busy person)

[Next let's use a sample REST API!](./2-use-sample-rest-api.md)