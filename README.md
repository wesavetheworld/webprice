webprice
========

Note: This script currently only works on pcpartpicker as amazon and ebay have updated their html. When I get round to it, I will update the search string. If you update it yourself, please submit a pull request. This script is bound to be out of date if the last commit hasn't been quite recent due to the nature of the project.

Please do not abuse this tool. It is designed for periodically checking websites for prices. Not for making constant requests.

Shell script to scrape pcpartpicker, ebay or amazon urls to check the latest cost. It can also take in a budget price and can tell you whether the price is above or below your budget. Highly dependent on the websites not changing the html.

I originally wrote it for PC partpicker, just waiting for my saved part list to fall below budget. It works on both saved builds and individual parts. I decided to make it more generic to cover some of the big websites. If anyone has any suggestions for others to add I'd be happy to do it, assuming they are reasonably popular. Otherwise you can just fork it.

You could quite easily pipe the output from this into some sort of notification for when a build or part falls below a certain price.

Script can be run alone using hard coded values like so 
                                                                                                
    $ webprice                                                                                   

It can also be run with an URL to check quickly
                                                                                                
    $ webprice http://uk.pcpartpicker.com/user/maxhebditch/saved/yxgFf7  

This only works if the link is quite short, otherwise need to put it in quotes `"URL"` to avoid stuff like `&` interfering and causing a `parse error`. This is probably best practise for websites with ugly URLs compared to pcpartpicker.

    $ webprice "http://www.amazon.co.uk/Untrue-Burial/dp/B000WTBMBK/ref=sr_1_1?s=music&ie=UTF8&qid=1407847596&sr=1-1&keywords=untrue+burial" 

or can give price compared to hard coded budget `$budget` difference with a `-b` flag.  $ webprice -b                                                                                Or a budget can be provide inline to over rule default budget.
                                                                                                
    $ webprice -b 600 http://www.amazon.co.uk/Untrue-Burial/dp/B000WTBMBK                        

The flags can be mixed up too

    $ webprice "http://www.amazon.co.uk/Untrue-Burial/dp/B000WTBMBK" 600 -b 

Using a `-l` flag
                                                                                                
    $ webprice -l                                                                                

the result will be logged in a csv file in the following directory
                                                                                                
    ~/scratch/logs/                                                                              

Which can be changed using the `$loglocation` variable

If the directory doesn't exist the script will tell you. Directory can be changed easily.
The file name is dependent on the product name in the URL.

The `-l` flag can be combined with the `-b` flag to log the price against your budget

    $ webprice -lb 500 "http://www.amazon.co.uk/Untrue-Burial/dp/B000WTBMBK/ref=sr_1_1?s=music&ie=UTF8&qid=1407847596&sr=1-1&keywords=untrue+burial"  

To log only with no terminal feedback the quiet flag, `-q`, can be used with the log flag `-l`
                                                                                                
    $ webprice -ql

This would be the best option for setting up a cron job.

Currency is also hard coded but can be changed in the variable `$currency`.

##Todo                                                                                            
3. Graph price changes with time
4. Add option to email/notify with price change
1. ~~Make it a more generic website scraping tool~~
5. ~~Ability for two flags: i.e. -bl for quiet and budget set values~~
6. ~~Variable for currency~~
7. ~~Variable for save location~~
8. ~~Robust URL parsing~~
9. ~~pcpartpicker parts~~
