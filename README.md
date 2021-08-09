# LinkedIn-Jobs-Web-Scraping-Java
## Web Scraping using Java Jsoup Html Parser : LinkedIn Jobs 


### Java Code
```java
              String url="https://www.linkedin.com/jobs/search/?keywords=tech&location=new%20york&position=1&pageNum=0";
              Document doc = Jsoup.connect(url).get();  
     
              Elements ul=doc.select("ul.jobs-search__results-list");
              Elements li = ul.select("li");
                        
              //Solution 1  - Accessing Single Element
              
              String src=li.eq(0).select("img.artdeco-entity-image").attr("data-delayed-url");
      	      String src2=li.eq(0).select("img.artdeco-entity-image").attr("data-ghost-url");    	           	    
      	      String href= li.eq(0).select(".base-card__full-link").attr("href");              
                    	      
      	      System.out.println("src : " + src);          	        	    
      	      System.out.println("src2 : " + src2);            	    
      	      System.out.println("href : " + href ); 
      	              
              // Solution 2  - Accessing Every Element using loop
      	      int i=1;
              for (Element item : li) {  
                        	           	    
            	    String JobTitle= item.getElementsByClass("base-search-card__title").text();
            	    
            	    //Please note : LinkedIn used data-delayed-url & data-ghost-url instead of src attribute 
            	    String ImgSrc1=item.select("img.artdeco-entity-image").attr("data-delayed-url");
            	    String ImgSrc2=item.select("img.artdeco-entity-image").attr("data-ghost-url");
            	           	    
            	    String hyperLink= item.select(".base-card__full-link").attr("href");
            	    
            	    System.out.println("Job : " + i); 
            	    System.out.println("Title : " + JobTitle);          	        	    
            	    System.out.println("Img Src 1 : " + ImgSrc1);  
            	    System.out.println("Img Src 1 : " + ImgSrc2);          	    
            	    System.out.println("Href : " + hyperLink );   
            	    System.out.println("");
            	   i++;
            	} 
                                              	          	     	      
          } catch (IOException e) {
              e.printStackTrace();
          }
```



## Output
```
Job : 1
Title : Product Strategy & Analytics Associate
Img Src 1 : https://media-exp1.licdn.com/dms/image/C510BAQGCdThXIss7UQ/company-logo_100_100/0/1539940587971?e=1636588800&v=beta&t=Omf-HbtMbuMUx_zvlf7j5A_UH5xKoavSuCY8JNrsPeI
Img Src 1 : https://static-exp1.licdn.com/sc/h/9a9u41thxt325ucfh5z8ga4m8
Href : https://www.linkedin.com/jobs/view/product-strategy-analytics-associate-at-tiktok-2673509867?refId=0ceT28kTvBIb2MLvqW9hEQ%3D%3D&trackingId=aijU9gSacDUdUKNvT3BZ%2Fg%3D%3D&position=1&pageNum=0&trk=public_jobs_jserp-result_search-card

Job : 2
Title : Creative Strategist, Brand Studio
Img Src 1 : https://media-exp1.licdn.com/dms/image/C4D0BAQHiNSL4Or29cg/company-logo_100_100/0/1519856215226?e=1636588800&v=beta&t=2h5cg3GQHW3DQHack9CExMCx1FtveDfCxAj8nyYFQ-c
Img Src 1 : https://static-exp1.licdn.com/sc/h/9a9u41thxt325ucfh5z8ga4m8
Href : https://www.linkedin.com/jobs/view/creative-strategist-brand-studio-at-google-2670343239?refId=0ceT28kTvBIb2MLvqW9hEQ%3D%3D&trackingId=TbptS54Q1K9Mp2%2FYR9MbNA%3D%3D&position=2&pageNum=0&trk=public_jobs_jserp-result_search-card

Job : 3
Title : VP, Strategy
Img Src 1 : https://media-exp1.licdn.com/dms/image/C4D0BAQFsTOeDD1vYRw/company-logo_100_100/0/1530537679784?e=1636588800&v=beta&t=JRnT3wVsdSE67SlDrHjt7flSD7klhZZ41HNmLB2dRvk
Img Src 1 : https://static-exp1.licdn.com/sc/h/9a9u41thxt325ucfh5z8ga4m8
Href : https://www.linkedin.com/jobs/view/vp-strategy-at-soulcycle-inc-2672408564?refId=0ceT28kTvBIb2MLvqW9hEQ%3D%3D&trackingId=BxBPyF6Afn%2FTDNb3Rx%2BIfA%3D%3D&position=3&pageNum=0&trk=public_jobs_jserp-result_search-card
```

