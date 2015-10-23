curl -XPOST localhost:9200/cars/transcations/_bulk --data-binary "@carsInfo"

{ "index" : {}}
{ "price" : 10000, "color" : "red", "make" : "honda", "sold" : "2014-10-28"}
{ "index" : {}}
{ "price" : 20000, "color" : "red", "make" : "honda", "sold" : "2014-11-05"}
{ "index" : {}}
{ "price" : 30000, "color" : "green", "make" : "ford", "sold" : "2014-05-18"}
{ "index" : {}}
{ "price" : 15000, "color" : "blue", "make" : "toyota", "sold" : "2014-07-02"}
{ "index" : {}}
{ "price" : 12000, "color" : "red", "make" : "honda", "sold" : "2014-10-28"}
{ "index" : {}}
{ "price" : 18000, "color" : "blue", "make" : "honda", "sold" : "2014-11-28"}
{ "index" : {}}
{ "price" : 80000, "color" : "green", "make" : "ford", "sold" : "2014-12-25"}
{ "index" : {}}
{ "price" : 25000, "color" : "blue", "make" : "honda", "sold" : "2014-10-05"}
{ "index" : {}}
{ "price" : 35000, "color" : "red", "make" : "ford", "sold" : "2014-10-28"}
