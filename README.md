# Overview

See the technical note [Liquidity Math in Uniswap v3](http://atiselsts.github.io/pdfs/uniswap-v3-liquidity-math.pdf) and the [Uniswap v3 whitepaper](https://uniswap.org/whitepaper-v3.pdf) for the description of the purpose of this code.

See the full project report at [GHOOK_Bachelor_Project_Report.pdf](https://github.com/Loris-EPFL/uniswap-v3-volatility-BA5/files/13778318/GHOOK_Bachelor_Project_Report.pdf)

For a Jupyter Notebook version of the code, see [yj's](https://github.com/uniyj) work here: https://github.com/uniyj/uni-v3-peri/tree/main/atiselsts-uniswap-v3-liquidity-math.

Have questions? Feel free to contact me via email atis.elsts@gmail.com or DM (https://twitter.com/atiselsts_eth). I'm also offering paid consultations on this topic.

## Contents

* [`uniswap-v3-liquidity-math.py`](uniswap-v3-liquidity-math.py) - implementation of the equations and examples from the "Liquidity Math in Uniswap v3" paper
* [`subgraph-liquidity-query-example.py`](subgraph-liquidity-query-example.py) - query the Uniswap v3 subgraph information to show the amounts locked in the current tick range of the USDC/WETH 0.3% pool
* [`subgraph-liquidity-range-example.py`](subgraph-liquidity-range-example.py) - shows the amounts locked in all ticks with nonzero `liquidityNet` in the USDC/WETH 0.3% pool
* [`subgraph-liquidity-positions-example.py`](subgraph-liquidity-positions-example.py) - shows the amounts locked in all active positions in the USDC/WETH 0.3% pool

## Installation and usage


Some scripts need the `gql` Python module. Install this dependency with:

    pip install -r requirements.txt

Execute from the command line, for example with:

    ./subgraph-liquidity-range-example.py

## Example outputs

### Example output of `uniswap-v3-liquidity-math.py`

```
Example 1: how much of USDC I need when providing 2 ETH at this price and range?
amount of USDC y=5076.10
p_a=1500.00 (75.00% of P), p_b=2500.00 (125.00% of P)

Example 2: I have 2 ETH and 4000 USDC, range top set to 3000 USDC. What's the bottom of the range?
lower bound of the price p_a=1333.33

Example 3: Using the position created in Example 2, what are asset balances at 2500 USDC per ETH?
Amount of ETH x=0.85 amount of USDC y=6572.89
delta_x=-1.15 delta_y=2572.89
Amount of ETH x=0.85 amount of USDC y=6572.89
```

### Example output of `subgraph-liquidity-query-example.py`

```
L=22510401004259913887
tick=195879
Current price: 0.000321 WETH for 1 USDC (3115.361406 USDC for 1 WETH)
Amounts at the current tick range: 1318490.67 USDC and 785.63 WETH
```

### Example output of `subgraph-liquidity-range-example.py`

```
...
tick=195660 price=3184.336897 USDC for WETH
        1193.68 WETH locked (potentially worth 3789699.28 USDC)
tick=195720 price=3165.289029 USDC for WETH
        1199.90 WETH locked (potentially worth 3786639.86 USDC)
tick=195780 price=3146.355100 USDC for WETH
        1218.77 WETH locked (potentially worth 3823192.07 USDC)
tick=195840 price=3127.534429 USDC for WETH
        Current tick, both assets present!
        1332170.50 USDC and 781.24 WETH remaining in the current tick range
        potentially 3770791.99 USDC or 1209.30 WETH in total in the current tick range
tick=195900 price=3108.826338 USDC for WETH
        3748424.25 USDC locked (potentially worth 1209.36 WETH)
tick=195960 price=3090.230154 USDC for WETH
        3782324.42 USDC locked (potentially worth 1227.64 WETH)
tick=196020 price=3071.745208 USDC for WETH
        3762895.47 USDC locked (potentially worth 1228.68 WETH)
tick=196080 price=3053.370833 USDC for WETH
        3740185.70 USDC locked (potentially worth 1228.62 WETH)
...
```
