# A Simple Spark program in Jupyter  
  ### Running a simple program to calculate the value of pi.  
    
  To launch Jupyter Notebook, command `pyspark` in the terminal  
  In the browser, create a new python notebook by selecting New --> Python3.  
  Running the below code should return the value of pi
  
    import random  
    num_samples = 100000000  
    def inside(p):       
    x, y = random.random(), random.random()  
    return x*x + y*y < 1  
    count = sc.parallelize(range(0, num_samples)).filter(inside).count()  
    pi = 4 * count / num_samples  
    print(pi)  
  
    
