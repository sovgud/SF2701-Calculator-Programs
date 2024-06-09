# SF2701 TI-84 Calculator Programs

Welcome to the repository for TI-84 calculator programs tailored for the SF2701 Financial Mathematics course at KTH Royal Institute of Technology. These programs are designed to closely align with exam questions, potentially saving you a significant amount of time during your exams. All programs are original work, provided as-is, with no warranty or responsibility from the author.

## How to Use

1. Download **TI Connect™ CE** from the [official website](https://education.ti.com/en/products/computer-software/ti-connect-ce-sw) and install it on your computer.
2. Follow the instructions to transfer the programs to your calculator.
3. On your calculator, press **PRGM** to display the **PRGM EXEC** menu. The programs in your calculator will appear in this menu. Select the program you want to use and press **ENTER**.
4. Enter the values for the required variables as prompted. See specific instructions for each program below.
5. Receive the computed answer.

Note: The programs modify and use variables in the calculator. It is best to avoid manually changing the values of any variables.

## Compatibility

The programs are written for the TI-84 Plus C Silver Edition. According to online sources, they should work on all calculators in the TI-83/84 series.

## Programs

### Binomial Model Programs

All programs starting with "A" are for the binomial models, which usually appear in the first exam question.

#### ACOMP

This program must be executed first before running any other programs for binomial models, as it sets the necessary variables $u$, $d$, $q$ and $1+R$.

Converts continuous compounding interest rate to variables used in the binomial model.

**Input Variables**:
| Variable   | Description                                    |
| ---------- | ---------------------------------------------- |
| $\Delta t$ | Length of time step in years                   |
| $\sigma$   | Volatility per annum                           |
| $r$        | Continuous compounding interest rate per annum |

**Output**: $u$, $d$, $q$, $1+R$

#### APRICEST

Computes the price tree of the risky asset in a binomial model with discrete proportional dividends.

**Input Variables**:
| Variable | Description                                                      |
| -------- | ---------------------------------------------------------------- |
| $T$      | Number of periods                                                |
| $s$      | Initial price of the risky asset                                 |
| $\delta$ | Dividend rate per time step (set to 0 if there are no dividends) |

**Output**: The price tree of the risky asset, starting from $t=0$. Each row represents one scenario in the format $\{S_{t-}, S_t\}$. "---" indicates the end of a time step, and you need to press enter to start the next one.

#### APRICEX

Computes the price tree of a European/American call/put option in a binomial model with discrete proportional dividends.

**Note**: For American call options, exercise will always happen before dividend payment. For American put options, exercise will always happen after dividend payment.

**Input Variables**:
| Variable | Description                                                      |
| -------- | ---------------------------------------------------------------- |
| $T$      | Number of periods                                                |
| $s$      | Initial price of the risky asset                                 |
| $K$      | Strike price                                                     |
| $\delta$ | Dividend rate per time step (set to 0 if there are no dividends) |

**Output**: The price tree of the selected option, starting from $t=T$. Each row represents one scenario. For American options, the first number is the price if exercised, and the second number is the price if the option is kept. "---" indicates the end of a time step, and you need to press enter to start the next one. The price at $t=0$ is the last displayed number.

#### APORT

Computes the replicating portfolio of a European/American call/put option in a binomial model **without** dividends.

**Input Variables**:
| Variable | Description                      |
| -------- | -------------------------------- |
| $T$      | Number of periods                |
| $s$      | Initial price of the risky asset |
| $K$      | Strike price                     |

**Output**: The replicating portfolio of the selected option, starting from $t=T$. Each row represents one scenario in the format $\{V^h_t, x_t, y_t\}$. "---" indicates the end of a time step, and you need to press enter to start the next one.

### Other Financial Programs

#### BBS

Computes the price of a European call or put option under the Black-Scholes market model.

#### BIMPVOL

Estimates the volatility of the Black-Scholes market model using the price of a European call option.

#### CZR2ZP

Computes zero bond prices from the term structure.

#### CBP2ZR

Computes the term structure from the price of zero-coupon bonds and fixed coupon bonds.

#### CINTDEVS

Contains multiple functions:

- Zero coupon bond price: Computes the price of a zero-coupon bond with maturity $T$ and strike $K$.
- Fixed coupon bond price: Computes the price of a fixed coupon bond with maturity $T$, strike $K$, and coupon $c$.
- FRA price: Computes the price of a forward rate agreement (FRA) with continuous rate $r$ where money is borrowed at $T_1$ and returned at $T_2$.
- Fixed coupon rate: Computes the continuous spot rate $r$ of a fixed coupon bond given maturity $T$, strike $K$, and price $P$.
- FRA rate: Computes the continuous rate $r$ of a forward rate agreement.
- Swap price: Computes the value of a swap viewed from the perspective of the fixed coupon payer. $R$ is the simple annual swap rate; $T_{\text{max}}-t$ is the number of remaining payments. $r(t,T)$ from $T=t+1$: zero rates for the remaining payments.
- Swap rate: Computes the swap rate of a swap quoted per annum using simple annual compounding.

**Notes**:

- `CZR2ZP` and `CBP2ZR` store zero-coupon bond prices and spot rates in the list variables `ZCBP` and `ZCBR`, respectively. These lists are used by `CINTDEVS`, so you need to run `CZR2ZP` or `CBP2ZR` before using `CINTDEVS`. The exception is the "Swap price" function in `CINTDEVS`, where you need to provide a new term structure, as is usually the case in exam questions.
- The programs assume $T=1, 2, 3, \ldots$. If your term structure uses different formats, the programs may not work correctly.
- Be aware of the differences between spot rates, simple rates, and forward rates.


## Examples
### Homework 1 spring 2018 1(a)
1. (a) Compute the price of a European call option written on a non-dividend-paying stock. The current stock price is $ $100$ and the volatility of the stock price is $30$%. The maturity of the option is in nine months and the strike price is $ $95$. The risk free interest rate with continuous compounding is $2$% per annum. You should use a three period binomial model to price the option.
Also compute the replicating portfolio.

#### Solution:

![!](/examples/2018HW1-1a-ACOMP1.png) 
![!](/examples/2018HW1-1a-ACOMP2.png)

We have that 

$$
\begin{aligned}
T & =9 / 12=3 / 4 \\
\Delta t & =T / 3=1 / 4 \\
u & =e^{\sigma \sqrt{\Delta t}} \approx 1.1618 \\
d & =e^{-\sigma \sqrt{\Delta t}} \approx 0.8607
\end{aligned}
$$


![!](/examples/2018HW1-1a-APRICEST1.png) 
![!](/examples/2018HW1-1a-APRICEST2.png) 
![!](/examples/2018HW1-1a-APRICEST3.png) 
![!](/examples/2018HW1-1a-APRICEST4.png) 
![!](/examples/2018HW1-1a-APRICEST5.png)

and the tree for the stock price is therefore

$$
\begin{array}{rrrr} 
& & & 156.8312 \\
& & 134.9859 &  \\
& 116.1834 & & 116.1834 \\
100.0000  & &100.0000  & \\
& 86.0708 & & 86.0708 \\
& & 74.0818 & \\
& & & 63.0708 \\
\end{array}
$$


![!](/examples/2018HW1-1a-APRICEX1.png) 
![!](/examples/2018HW1-1a-APRICEX2.png) 
![!](/examples/2018HW1-1a-APRICEX3.png) 
![!](/examples/2018HW1-1a-APRICEX4.png) 
![!](/examples/2018HW1-1a-APRICEX5.png) 
![!](/examples/2018HW1-1a-APRICEX6.png) 

Now the option price tree can be computed using

$$
q=\frac{e^{r \Delta t}-d}{u-d} \approx 0.4792
$$

and the discount factor

$$
\frac{1}{e^{r \Delta t}} \approx \frac{1}{1.0050}
$$

and the result is

$$
\begin{array}{rrrr} 
& & & 61.8312 \\
& & 40.4597& \\
 & 24.5263 & & 21.1834 \\
14.1905 & & 10.1008 & \\
&4.8163 & & 0.0000 \\
& & 0.0000 & \\
& & &0.0000
\end{array}
$$

The price of the option is thus 14.1905.

![!](/examples/2018HW1-1a-APORT1.png) 
![!](/examples/2018HW1-1a-APORT2.png) 
![!](/examples/2018HW1-1a-APORT3.png) 
![!](/examples/2018HW1-1a-APORT4.png) 
![!](/examples/2018HW1-1a-APORT5.png)    

For the replicating portfolio we obtain

$$
\begin{array}{lll} 
 & & \begin{aligned} & x=-94.5262 \\
 & y=1.0000  \end{aligned} \\
 &  \begin{aligned} & x=-76.2915 \\ 
 & y=0.8677 \end{aligned} & \\
\begin{aligned} & x=-51.2637 \\ 
& y=0.6545 \end{aligned}  & & \begin{aligned} & x=-60.2465 \\ 
& y=0.7035  \end{aligned}\\
 &  \begin{aligned} &x=-28.7271 \\ 
 & y=0.3897  \end{aligned} & \\
 & & \begin{aligned} & x=0.0000 \\ 
 & y=0.0000  \end{aligned} \\
\end{array}
$$

Here $x$ is the amount of money in the bank and $y$ is the number of stock you own. Note that $y=\Delta$, and that once you have $y$ it is easy to solve for $x$.


### Exam 2020-05-27 3
3 Suppose the following bonds are trading in the market today (prices in £ ):
- A zero coupon bond with face value 100 and maturity in one year trades at 97.00 ;
- A coupon bond with face value 100 , maturity in two years, and a coupon of $3$% per annum paid annually trades at 98.91 ;
- A coupon bond with face value 100 , maturity in three years, and a coupon of $4$% per annum paid annually trades at 99.86.

a) Compute the current term structure; i.e. the continuously compounded spot rates for one, two and three years.

b) Two parties want to set up a forward rate agreement (FRA) for the third year on 1 million (i.e. money are to be borrowed two years from now and returned three years from now). Decide what the borrowing (lending) rate should be set to in order for the current value of the contract to equal zero; quote the rate per annum with continuous compounding.

c) One year ago two parties entered a four year fixed-for-floating swap agreement, where one-year LIBOR was agreed to be exchanged for a fixed swap rate $R_s$, with annual coupon payments (in total four); the notational principal was set to 1 million and the swap rate to $R_s=3.5$% quoted per annum using simple annual compounding. Give the value of this contract today after the first coupon payments have been made (make sure to specify to which part the contract has a positive value).

#### a) Use CBP2ZR

![!](/examples/20200527-3A-CBP2ZR1.png)
![!](/examples/20200527-3A-CBP2ZR2.png)
![!](/examples/20200527-3A-CBP2ZR3.png)
![!](/examples/20200527-3A-CBP2ZR4.png)
![!](/examples/20200527-3A-CBP2ZR5.png)
![!](/examples/20200527-3A-CBP2ZR6.png)
![!](/examples/20200527-3A-CBP2ZR7.png)

Answer: $r(0, 1) = 0.030, r(0, 2) = 0.035, r(0, 3) = 0.040$

#### b) Use CINTDEVS, FRA rate

![!](/examples/20200527-3B-CINTDEVS1.png)
![!](/examples/20200527-3B-CINTDEVS2.png)

Answer: $0.049$

#### c) Use CINTDEVS, Swap price

![!](/examples/20200527-3C-CINTDEVS1.png)

Answer: $-15468$

### Exam 2021-06-02 3a)-b)

3 a) Suppose the current term structure (i.e. the continuously compounded spot rates) is given by:

$$
\begin{array}{r|l}
T & r(0,T) \\
\hline
1 & 1.5 \\% \\
2 & 1.8 \\% \\
3 & 2.0 \\%
\end{array}
$$

Compute the current price of the zero coupon bonds with maturity in one, two and three years, respectively.

b) Consider two parties who enter today a fixed-for-floating swap agreement where one-year LIBOR is exchanged for a fixed swap rate $R_s$ with annual coupon payments; there are in total three payments taking place in one, two and three years from now. The notational principal is 1 million. Given the term structure in a), specify $R_s$ so that the agreement has zero value when entered; quote $R_s$ per annum using simple annual compounding.

c) Suppose that at time $t=1$, the market has evolved so that the term structure then takes the following form:

$$
\begin{array}{r|l}
T & r(0,T) \\
\hline
2 & 3.0 \\% \\
3 & 4.0 \\%
\end{array}
$$

Suppose that the agreement in b) was entered at time $t=0$ for the fair rate computed in b). Viewed from the perspective of the party receiving the floating leg, given the above term structure, what is the value of the contract at time $t=1$ right after the coupon payments have been made?



#### a) Use CZR2ZP
![!](/examples/20210602-3a-CZR2ZP1.png) 

Answer: $p(0, 1) = 0.985, p(0, 2) = 0.965, p(0, 3) = 0.942$

#### b) Use CINTDEVS, Swap rate
![!](/examples/20210602-3b-CINTDEVS1.png)
![!](/examples/20210602-3b-CINTDEVS2.png) 

Answer: $R=0.02$.





