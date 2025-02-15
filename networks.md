````
import * as dotenv from 'dotenv';

import { HardhatUserConfig } from 'hardhat/config';
import '@nomiclabs/hardhat-etherscan';
import '@nomiclabs/hardhat-waffle';
import '@typechain/hardhat';
import 'hardhat-gas-reporter';
import 'solidity-coverage';

import './tasks/deploy';

dotenv.config();

const config: HardhatUserConfig = {
  solidity: '0.8.4',
  paths: {
    artifacts: './frontend/src/artifacts'
  },
  networks: {
    hardhat: {
      mining: {
        auto: false,
        interval: 1000
      }
    },
    ropsten: {
      url: process.env.ROPSTEN_URL || '',
      accounts:
        process.env.TEST_ETH_ACCOUNT_PRIVATE_KEY !== undefined
          ? [process.env.TEST_ETH_ACCOUNT_PRIVATE_KEY]
          : []
    }
  },
  gasReporter: {
    enabled: process.env.REPORT_GAS !== undefined,
    currency: 'USD'
  },
  etherscan: {
    apiKey: process.env.ETHERSCAN_API_KEY
  }
};

export default config;
```

```
ETHERSCAN_API_KEY=<U5BJX2J29TUET2KZQDD4JTWZ91SCQ5G456>
ROPSTEN_URL=https://eth-sepolia.g.alchemy./v2.io/<wpgYdj00Mll00w9xypcqM69iT8OTtVKQ> 
TEST_ETH_ACCOUNT_PRIVATE_KEY=<8f57996d8e8a6cefc49a76525c4cdf38fabe6ac5ff7c3aa6dc977cb69fecd0a5>

```
