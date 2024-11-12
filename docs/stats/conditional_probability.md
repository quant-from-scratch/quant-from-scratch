Before we move to the next time series topic, let's review the concept of conditional probability. Conditional probability is an important concept incorporated in the topic we will discuss next. 

Let's use an example to explain conditional probability. Say we have a cookie jar with 20 cookies. Using the cookies' ingredients, the distribution of cookies is as follows:

**Figure 7. Cookie Distribution by Ingredients**

|           | Dark Chocolate |Milk Chocolate | White Chocolate |
| :---      | :---: | :---: | :---: |
| With Nuts |   6   |   4   |   2   |
| No Nuts   |   3   |   4   |   1   |


Now, given that we get a cookie with dark chocolate, what is the probability that this cookie contains nuts? This is a conditional probability question. In mathematic form, we can write $P(\text{cookie has nuts} \ | \ \text{cookie has dark chocolate})$. The "|" stands for "given." Instead of trying to get the answer by checking all 20 cookies, we only need to focus on nine cookies with dark chocolate now. Among these nine cookies, there are six cookies that have nuts. Hence, $P(\text{cookie has nuts} \ | \ \text{cookie has dark chocolate}) = 6 / 9$. We can see the above math operation reduces the sample space from 20 cookies to nine cookies for conditional probability.

In the formal math form, assuming we know event $A$ and event $B$ are all in the same sample space, the **conditional probability** that event $A$ will happen given that event $B$ happens is:

$$ P(A|B) $$

Please review the required reading on conditional probability to learn its properties and its relationship with joint probability and marginal probability.
