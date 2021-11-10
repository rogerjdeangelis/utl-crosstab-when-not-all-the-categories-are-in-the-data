# utl-crosstab-when-not-all-the-categories-are-in-the-data
Crosstab when not all the categories are in the data  
    Crosstab when not all the categories are in the data                                                                                
                                                                                                                                        
    github                                                                                                                              
    https://tinyurl.com/kamkmb22                                                                                                        
    https://github.com/rogerjdeangelis/utl-crosstab-when-not-all-the-categories-are-in-the-data                                         
                                                                                                                                        
    StackOverFlow                                                                                                                       
    https://tinyurl.com/4aue6bre                                                                                                        
    https://stackoverflow.com/questions/69070701/cross-tabulation-frequency-table-in-sas                                                
                                                                                                                                        
    Solution by                                                                                                                         
    Vaibhav Kabdwal                                                                                                                     
    https://stackoverflow.com/users/11781859/vaibhav-kabdwal                                                                            
                                                                                                                                        
    Macros                                                                                                                              
    https://tinyurl.com/jek5z8kw                                                                                                        
    https://github.com/rogerjdeangelis/utl-macros-used-in-many-of-rogerjdeangelis-repositories                                          
                                                                                                                                        
    /*                   _                                                                                                              
    (_)_ __  _ __  _   _| |_                                                                                                            
    | | `_ \| `_ \| | | | __|                                                                                                           
    | | | | | |_) | |_| | |_                                                                                                            
    |_|_| |_| .__/ \__,_|\__|                                                                                                           
            |_|                                                                                                                         
                                                                                                                                        
    */                                                                                                                                  
                                                                                                                                        
    data have;                                                                                                                          
      input FY TC;                                                                                                                      
    cards4;                                                                                                                             
    2013 1                                                                                                                              
    2013 8                                                                                                                              
    2014 5                                                                                                                              
    2014 12                                                                                                                             
    2013 6                                                                                                                              
    2013 13                                                                                                                             
    2015 7                                                                                                                              
    2015 14                                                                                                                             
    2016 1                                                                                                                              
    2016 8                                                                                                                              
    2015 5                                                                                                                              
    2015 12                                                                                                                             
    2016 2                                                                                                                              
    2016 9                                                                                                                              
    2014 2                                                                                                                              
    2014 9                                                                                                                              
    2013 7                                                                                                                              
    2013 14                                                                                                                             
    2014 4                                                                                                                              
    2014 11                                                                                                                             
    2017 5                                                                                                                              
    2017 12                                                                                                                             
    2018 1                                                                                                                              
    2018 8                                                                                                                              
    2018 6                                                                                                                              
    2018 13                                                                                                                             
    2015 4                                                                                                                              
    2015 11                                                                                                                             
    2014 2                                                                                                                              
    2014 9                                                                                                                              
    2015 4                                                                                                                              
    2015 11                                                                                                                             
    2013 1                                                                                                                              
    2013 8                                                                                                                              
    ;;;;                                                                                                                                
    run;quit;                                                                                                                           
                                                                                                                                        
    /*           _               _                                                                                                      
      ___  _   _| |_ _ __  _   _| |_                                                                                                    
     / _ \| | | | __| `_ \| | | | __|                                                                                                   
    | (_) | |_| | |_| |_) | |_| | |_                                                                                                    
     \___/ \__,_|\__| .__/ \__,_|\__|                                                                                                   
                    |_|                                                                                                                 
                                                                                                                                        
    Note T10 and T3 are not in the data.                                                                                                
                                                                                                                                        
    Also note we have Two T1=1                                                                                                          
                                                                                                                                        
      n-1(first ob) and n=34(last ob) thus we have count=2                                                                              
                                                                                                                                        
    WORK.WANT total obs=6 10NOV2021:15:48:37                                                                                            
                                                                                                                                        
    Obs   FY   TC1           TC2  TC3  TC4  TC5  TC6  TC7  TC8  TC9  TC10  TC11  TC12  TC13  TC14                                       
                                                                                                                                        
     1   2013   2 n=1 n=34    0    0    0    0    1    1    4    0     0     0     0     2     2                                        
     2   2014   0             2    0    1    1    0    0    0    4     0     2     2     0     0                                        
     3   2015   0             0    0    2    1    0    1    0    0     0     4     2     0     2                                        
     4   2016   1             1    0    0    0    0    0    2    2     0     0     0     0     0                                        
     5   2017   0             0    0    0    1    0    0    0    0     0     0     2     0     0                                        
     6   2018   1 n=22        0    0    0    0    1    0    2    0     0     0     0     2     0                                        
                                                                                                                                        
               _       _   _                                                                                                            
     ___  ___ | |_   _| |_(_) ___  _ __                                                                                                 
    / __|/ _ \| | | | | __| |/ _ \| `_ \                                                                                                
    \__ \ (_) | | |_| | |_| | (_) | | | |                                                                                               
    |___/\___/|_|\__,_|\__|_|\___/|_| |_|                                                                                               
                                                                                                                                        
    Note TC does not have to be numeric for do_over to work;                                                                            
    Forinstance if 1=A, 2=B..14=N                                                                                                       
    You will need to know which of the 14 letters is missing and create this template array array                                       
                                                                                                                                        
    %array(ltr,values=a b c d e f g h i j k l m n)                                                                                      
                          v             v                                                                                               
                      not in data     not in data                                                                                       
    */                                                                                                                                  
                                                                                                                                        
                                                                                                                                        
                                                                                                                                        
    %array(_tc,values=1-14);                                                                                                            
    %put &=_tc6;                                                                                                                        
    %put &=_tcn;                                                                                                                        
                                                                                                                                        
    /*                                                                                                                                  
     _TC6=6                                                                                                                             
     _TCN=14                                                                                                                            
    */                                                                                                                                  
                                                                                                                                        
    proc sql;                                                                                                                           
      create                                                                                                                            
         table want as                                                                                                                  
      select                                                                                                                            
         fy                                                                                                                             
        ,%do_over(_tc,phrase=%str(sum(tc=?) as tc?),between=comma)                                                                      
      from                                                                                                                              
         have                                                                                                                           
      group                                                                                                                             
         by fy                                                                                                                          
    ;quit;                                                                                                                              
                                                                                                                                        
    * cleanup;                                                                                                                          
    %arraydelete(_tc);                                                                                                                  
    /*           _               _                                                                                                      
      ___  _   _| |_ _ __  _   _| |_                                                                                                    
     / _ \| | | | __| `_ \| | | | __|                                                                                                   
    | (_) | |_| | |_| |_) | |_| | |_                                                                                                    
     \___/ \__,_|\__| .__/ \__,_|\__|                                                                                                   
                    |_|                                                                                                                 
                                                                                                                                        
    Up to 40 obs WORK.WANT total obs=6 10NOV2021:16:28:51                                                                               
                                                                                                                                        
    Obs   FY   TC1  TC2  TC3  TC4  TC5  TC6  TC7  TC8  TC9  TC10  TC11  TC12  TC13  TC14                                                
                                                                                                                                        
     1   2013   2    0    0    0    0    1    1    2    0     0     0     0     1     1                                                 
     2   2014   0    2    0    1    1    0    0    0    2     0     1     1     0     0                                                 
     3   2015   0    0    0    2    1    0    1    0    0     0     2     1     0     1                                                 
     4   2016   1    1    0    0    0    0    0    1    1     0     0     0     0     0                                                 
     5   2017   0    0    0    0    1    0    0    0    0     0     0     1     0     0                                                 
     6   2018   1    0    0    0    0    1    0    1    0     0     0     0     1     0                                                 
                                                                                                                                        
                                      _                                                                                                 
      __ _  ___ _ __     ___ ___   __| | ___                                                                                            
     / _` |/ _ \ `_ \   / __/ _ \ / _` |/ _ \                                                                                           
    | (_| |  __/ | | | | (_| (_) | (_| |  __/                                                                                           
     \__, |\___|_| |_|  \___\___/ \__,_|\___|                                                                                           
     |___/                                                                                                                              
    */                                                                                                                                  
                                                                                                                                        
                                                                                                                                        
    If you want the code                                                                                                                
                                                                                                                                        
    data _null_;                                                                                                                        
        %do_over(_tc,phrase=%str(put ",sum(tc=?) as tc?" ;))  ;                                                                         
    run;quit;                                                                                                                           
                                                                                                                                        
    options ls=96;                                                                                                                      
                                                                                                                                        
    ,sum(tc=1) as tc1                                                                                                                   
    ,sum(tc=2) as tc2                                                                                                                   
    ,sum(tc=3) as tc3                                                                                                                   
    ,sum(tc=4) as tc4                                                                                                                   
    ,sum(tc=5) as tc5                                                                                                                   
    ,sum(tc=6) as tc6                                                                                                                   
    ,sum(tc=7) as tc7                                                                                                                   
    ,sum(tc=8) as tc8                                                                                                                   
    ,sum(tc=9) as tc9                                                                                                                   
    ,sum(tc=10) as tc10                                                                                                                 
    ,sum(tc=11) as tc11                                                                                                                 
    ,sum(tc=12) as tc12                                                                                                                 
    ,sum(tc=13) as tc13                                                                                                                 
    ,sum(tc=14) as tc14                                                                                                                 
                                                                                                                                        
                                                                                                                                        
