webprice
========

Shell script to scrape pcpartpicker, ebay or amazon urls to check the latest total cost.        
It can also take in a budget price and can tell you whether the price is above or below your    
budget.                                                                                         
                                                                                                
Script can be run alone using hard coded values like so                                         
                                                                                                
    $ webprice                                                                                   
                                                                                                
It can also be run with an URL to check quickly                                                 
                                                                                                
    $ webprice http://www.amazon.co.uk/Untrue-Burial/dp/B000WTBMBK                               
                                                                                                
or can give price compared to hard coded  budget difference with a -b flag.                     
                                                                                                
    $ webprice -b                                                                                
                                                                                                
Or a budget can be provide inline                                                               
                                                                                                
    $ webprice -b 600 http://www.amazon.co.uk/Untrue-Burial/dp/B000WTBMBK                        
                                                                                                
Using a -l flag                                                                                 
                                                                                                
    $ webprice -l                                                                                
                                                                                                
the result will be logged in a csv file in the following directory                              
                                                                                                
    ~/scratch/logs/                                                                              
                                                                                                
Which can be changed using the $loglocation variable
    
If the directory doesn't exist the script will tell you. Directory can be changed easily.       
The file name is dependent on the product name in the URL.                                      
                                                                                                
To log only with no terminal feedback the quiet flag, -q, can be used with the log flag -l      
                                                                                                
    $ webprice -ql                                                                               
                                                                                                
This would be the best option for setting up a cron job                                         

Currency is also hard coded but can be changed in the variable $currency
                                                                                                
##Todo                                                                                            

1) Make it a more generic website scraping tool DONE                                            
2) Offer multiple websites/urls                                                                 
3) Graph price changes with time                                                                
4) Add option to email with price change                                                        
5) Ability for two flags: i.e. -qh for quiet and budget set values DONE                         
