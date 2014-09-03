Salary
======

Everyone at Bitmazk earns the same.

We don't know for how long we will be able to hold up this philosophy but as
long as we have less than 50 employees we are quite sure that everyone's work
will be equally important to the company's success.

This means that if you want to have a pay-rise, everyone will get a pay-rise
and obviously that has to be earned, otherwise we would probably go bankrupt
quickly.

We have a formula that determines how we handle pay-rises.

In simple words it goes like this: Every time we have one more month worth of
total salaries in the bank, we get a S$100 pay-rise.

To be more precise, here are some variables:

* `starting salary` - the first salary when the company was founded
* `payrise count` - the number of pay-rises that have been given when we will
  get the next pay-rise
* `total salary` - equals `starting salary * number of employees`
* `payrise amount` - we set this to S$100

In order to get a pay-rise, the equity of the company (cash in the bank plus
outstanding invoices) must equal::

    (total salary + (payrise amount * payrise count * number of employees))) * payrise_count

This is at the beginning of the month, after all of last month's outstanding
payables and salaries have been paid.

Example:

* Pay-rise count: `1`
* Starting salary: `S$4,200`
* Employees: `3`
* Total salary: `3 * S$4,200 = S$12,600`
* Necessary equity: `(S$12,600 + (S$100 * 1 * 3)) * 1 = S$12,900`

========= ====== ============ ============= ============== ================
Employees Salary Total salary Payrise count Payrise amount Necessary equity
========= ====== ============ ============= ============== ================
3         4200   12600        1             100            12900
3         4300   12900        2             100            26400
3         4400   13200        3             100            40500
3         4500   13500        4             100            55200
3         4600   13800        5             100            70500
3         4700   14100        6             100            86400
3         4800   14400        7             100            102900
3         4900   14700        8             100            120000
3         5000   15000        9             100            137700
========= ====== ============ ============= ============== ================
