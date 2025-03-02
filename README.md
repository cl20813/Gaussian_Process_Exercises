# Gaussian Process approximation.

The goal of this project is to approximate likelihood by using subset of data which follows gaussian process.

## How to read HDF file and NC file in Python.
-[See this](total_column_ozone/Read_save_ncfile.ipynb)

## Exercise 1: Simulate data using exponential kernel then attempt to fit only the variance using the Matérn kernel, and vice versa. 
  1. If we try to fit matern when exponential kernel is true, fitted variance will go to infinity to compensate matern's faster decaying speed.
  2. On the other hand, if we try to fit exponential kernel when true model is mater, fitted variance will go to 0 to compensate exp's slower decaying speed.

  -[Experiment result](https://github.com/cl20813/Gaussian-Process-approximation/blob/567fc1abc0f2e12e7582635b54813c3ec11268d6/Exercises/Fit%20matern_true%20exp.pdf)


Click the link to review expectation and variance of theta(variance).
[Click here](https://stats.stackexchange.com/questions/427332/variance-of-quadratic-form-for-multivariate-normal-distribution)


  
## Exercise 2: Using the eigen-values and eigen-vectors to assess the quality of the model.

  -[Experiment result](Exercises/Diagnostics_of_covariance_matrix_using_eigenvalue.ipynb)
  

## Exercise 3: Extension of exercise 2 to spatio-temporal covariance matrices in Stein(2004).

  -[Experiment result](Exercises/Spat_tmp_cov_exercise_stein_2004_python.ipynb)
  

## Exercise 4: Now we investigate the behavior of (eigen vector x complex exponential ) 

  -[Explanation](Exercises/Isometry_same_norm_spectrum_1_12.pdf)
  See the chapter 2.6 "Two corresponding Hilbert spaces" in Stein's book. Note that there is no randomness when working with spectral density.

  -[Python code](Exercises/Isometry_same_norm_spectrum_1_12.ipynb)

## Exercise 5: Now we investigate the behavior of (eigen vector x complex exponential ) 

1. Exercise 5-1: Observe the difference of isotrpoic model and anisotropic model.
2. Exercise 5-2: Let $f_1(w)= o(w^2)$ and $f_2(w)= o(w^4)$. If we look at $\biggl| \sum_j v_{jk} e^{i \omega x_j} \biggr|$, $f_2$ is lower than $f_1$ at w=0 and the difference decreases as w goes to high frequency. Here we use BLP for linear coefficients, $argmin_c  cov(  Z_0 - C^\top Z,  Z_0 - C^\top Z )   = \hat{C}= \Gamma^{-1} \gamma.$

3. Exercise 5-3: Observe that most of the variance of BLP is at high frequencies, another reason why we should focus on local behaviors.
   See "Predicting random fields", Stein (1999).

   -[Python code2](Exercises/Experiment5.ipynb)

## Exercise 6. Correlation and relative standard errors of empirical semi-variogram. 

  -[Explanation](Exercises/Experiment6_acf_semivariogram.pdf)
  
  -[Python code](Exercises/Experiment6_acf_semivarogram.ipynb)

## 03-01-2025
  

<100*8 data after sorting each data by longitude and latitude>  

params= [20, 8.25, 5.25, 0.2, 0.5, 5]
Full likelihood: 2172.70
Vecchia Maxmin: 2264
Vecchia Column: 1928

params= [60, 8.25, 5.25, 0.2, 0.5, 5]
Full likelihood: 2217         +35 
Vecchia Maxmin: 2273          +9
Vecchia Column: 1729          -199

<200*8 data after sorting each data by longitude and latitude>


params= [20, 8.25, 5.25, 0.2, 0.5, 5]
Full likelihood: 4174.860696545362                    21 seconds
Vecchia Maxmin: 4336.260475230565                     1 seconds
Vecchia Column: 3330. 329727                          0.1 seconds
 
params= [60, 8.25, 5.25, 0.2, 0.5, 5]
Full likelihood: 4297          +123         21 seconds
Vecchia Maxmin: 4439  	       +103         1
Vecchia Column: 3151	       -149 	    0.1


Other observations:
If I don't sort data by longitude and latitude, vecchia column is a lot worse. 
Conditioning on east is better than conditioning on west.
Clearly, conditioning on longitude column is better than using latitude slices. 
  


 


