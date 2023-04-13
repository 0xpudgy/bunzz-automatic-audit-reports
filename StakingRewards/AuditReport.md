# StakingRewards

## Summary

Number of lines: 1144 (+ 0 in dependencies, + 0 in tests)
Number of assembly lines: 0
Number of contracts: 10 (+ 0 in dependencies, + 0 tests) 

Number of optimization issues: 0
Number of informational issues: 34
Number of low issues: 10
Number of medium issues: 2
Number of high issues: 1
ERCs: ERC20

+----------------+-------------+-------+--------------------+--------------+--------------------+
|      Name      | # functions |  ERCS |     ERC20 info     | Complex code |      Features      |
+----------------+-------------+-------+--------------------+--------------+--------------------+
|  IERC20Permit  |      3      |       |                    |      No      |                    |
|     IERC20     |      6      | ERC20 |     No Minting     |      No      |                    |
|                |             |       | Approve Race Cond. |              |                    |
|                |             |       |                    |              |                    |
|    Address     |      13     |       |                    |      No      |      Send ETH      |
|                |             |       |                    |              |    Delegatecall    |
|                |             |       |                    |              |      Assembly      |
|   SafeERC20    |      7      |       |                    |      No      |      Send ETH      |
|                |             |       |                    |              | Tokens interaction |
| StakingRewards |      44     |       |                    |      No      |      Send ETH      |
|                |             |       |                    |              | Tokens interaction |
+----------------+-------------+-------+--------------------+--------------+--------------------+

## Contract Summary

+ Contract IStakingRewards
  - From IStakingRewards
    - balanceOf(address) (external)
    - claim() (external)
    - earned(address) (external)
    - exit() (external)
    - getRewardForDuration() (external)
    - lastTimeRewardApplicable() (external)
    - rewardPerToken() (external)
    - stake(uint256) (external)
    - unstake(uint256) (external)

+ Contract StakingRewards (Most derived contract)
  - From ReentrancyGuard
    - _nonReentrantAfter() (private)
    - _nonReentrantBefore() (private)
    - constructor() (internal)
  - From Pausable
    - _pause() (internal)
    - _requireNotPaused() (internal)
    - _requirePaused() (internal)
    - _unpause() (internal)
    - paused() (public)
  - From Context
    - _msgData() (internal)
    - _msgSender() (internal)
  - From Ownable
    - _checkOwner() (internal)
    - _transferOwnership(address) (internal)
    - owner() (public)
    - renounceOwnership() (public)
    - transferOwnership(address) (public)
  - From StakingRewards
    - _earned(address) (internal)
    - _lastTimeRewardApplicable() (internal)
    - _rewardPerToken() (internal)
    - balanceOf(address) (external)
    - claim() (public)
    - constructor(address,address,uint256) (public)
    - earned(address) (external)
    - exit() (public)
    - fund(uint256) (public)
    - getRewardForDuration() (external)
    - lastTimeRewardApplicable() (external)
    - recoverERC20(address,uint256) (external)
    - rewardPerToken() (external)
    - setRewardsDuration(uint256) (external)
    - stake(uint256) (public)
    - unstake(uint256) (public)

## Contract Function Summary

Contract IStakingRewards
Contract vars: []
Inheritance:: []
 
+----------------------------+------------+-----------+------+-------+----------------+----------------+
|          Function          | Visibility | Modifiers | Read | Write | Internal Calls | External Calls |
+----------------------------+------------+-----------+------+-------+----------------+----------------+
|     balanceOf(address)     |  external  |     []    |  []  |   []  |       []       |       []       |
|      earned(address)       |  external  |     []    |  []  |   []  |       []       |       []       |
|   getRewardForDuration()   |  external  |     []    |  []  |   []  |       []       |       []       |
| lastTimeRewardApplicable() |  external  |     []    |  []  |   []  |       []       |       []       |
|      rewardPerToken()      |  external  |     []    |  []  |   []  |       []       |       []       |
|       stake(uint256)       |  external  |     []    |  []  |   []  |       []       |       []       |
|      unstake(uint256)      |  external  |     []    |  []  |   []  |       []       |       []       |
|          claim()           |  external  |     []    |  []  |   []  |       []       |       []       |
|           exit()           |  external  |     []    |  []  |   []  |       []       |       []       |
+----------------------------+------------+-----------+------+-------+----------------+----------------+

+-----------+------------+------+-------+----------------+----------------+
| Modifiers | Visibility | Read | Write | Internal Calls | External Calls |
+-----------+------------+------+-------+----------------+----------------+
+-----------+------------+------+-------+----------------+----------------+

Contract StakingRewards
Contract vars: ['_owner', '_paused', '_NOT_ENTERED', '_ENTERED', '_status', 'stakingToken', 'rewardsToken', 'periodFinish', 'rewardRate', 'rewardsDuration', 'lastUpdateTime', 'rewardPerTokenStored', 'userRewardPerTokenPaid', 'rewards', 'totalSupply', 'balances']
Inheritance:: ['ReentrancyGuard', 'Pausable', 'Ownable', 'Context', 'IStakingRewards']
 
+---------------------------------------+------------+---------------------------------------------------+--------------------------------------------+-------------------------------------+------------------------------------------------------+-------------------------------------------------------------------------------------------------------------+
|                Function               | Visibility |                     Modifiers                     |                    Read                    |                Write                |                    Internal Calls                    |                                                External Calls                                               |
+---------------------------------------+------------+---------------------------------------------------+--------------------------------------------+-------------------------------------+------------------------------------------------------+-------------------------------------------------------------------------------------------------------------+
|             constructor()             |  internal  |                         []                        |              ['_NOT_ENTERED']              |             ['_status']             |                          []                          |                                                      []                                                     |
|         _nonReentrantBefore()         |  private   |                         []                        |          ['_ENTERED', '_status']           |             ['_status']             |               ['require(bool,string)']               |                                                      []                                                     |
|          _nonReentrantAfter()         |  private   |                         []                        |              ['_NOT_ENTERED']              |             ['_status']             |                          []                          |                                                      []                                                     |
|             constructor()             |  internal  |                         []                        |                     []                     |             ['_paused']             |                          []                          |                                                      []                                                     |
|                paused()               |   public   |                         []                        |                ['_paused']                 |                  []                 |                          []                          |                                                      []                                                     |
|          _requireNotPaused()          |  internal  |                         []                        |                     []                     |                  []                 |          ['paused', 'require(bool,string)']          |                                                      []                                                     |
|            _requirePaused()           |  internal  |                         []                        |                     []                     |                  []                 |          ['paused', 'require(bool,string)']          |                                                      []                                                     |
|                _pause()               |  internal  |                 ['whenNotPaused']                 |                     []                     |             ['_paused']             |           ['_msgSender', 'whenNotPaused']            |                                                      []                                                     |
|               _unpause()              |  internal  |                   ['whenPaused']                  |                     []                     |             ['_paused']             |             ['_msgSender', 'whenPaused']             |                                                      []                                                     |
|              _msgSender()             |  internal  |                         []                        |               ['msg.sender']               |                  []                 |                          []                          |                                                      []                                                     |
|               _msgData()              |  internal  |                         []                        |                ['msg.data']                |                  []                 |                          []                          |                                                      []                                                     |
|             constructor()             |  internal  |                         []                        |                     []                     |                  []                 |         ['_msgSender', '_transferOwnership']         |                                                      []                                                     |
|                owner()                |   public   |                         []                        |                 ['_owner']                 |                  []                 |                          []                          |                                                      []                                                     |
|             _checkOwner()             |  internal  |                         []                        |                     []                     |                  []                 |               ['_msgSender', 'owner']                |                                                      []                                                     |
|                                       |            |                                                   |                                            |                                     |               ['require(bool,string)']               |                                                                                                             |
|          renounceOwnership()          |   public   |                   ['onlyOwner']                   |                     []                     |                  []                 |         ['onlyOwner', '_transferOwnership']          |                                                      []                                                     |
|       transferOwnership(address)      |   public   |                   ['onlyOwner']                   |                     []                     |                  []                 |         ['_transferOwnership', 'onlyOwner']          |                                                      []                                                     |
|                                       |            |                                                   |                                            |                                     |               ['require(bool,string)']               |                                                                                                             |
|      _transferOwnership(address)      |  internal  |                         []                        |                 ['_owner']                 |              ['_owner']             |                          []                          |                                                      []                                                     |
|           balanceOf(address)          |  external  |                         []                        |                     []                     |                  []                 |                          []                          |                                                      []                                                     |
|            earned(address)            |  external  |                         []                        |                     []                     |                  []                 |                          []                          |                                                      []                                                     |
|         getRewardForDuration()        |  external  |                         []                        |                     []                     |                  []                 |                          []                          |                                                      []                                                     |
|       lastTimeRewardApplicable()      |  external  |                         []                        |                     []                     |                  []                 |                          []                          |                                                      []                                                     |
|            rewardPerToken()           |  external  |                         []                        |                     []                     |                  []                 |                          []                          |                                                      []                                                     |
|             stake(uint256)            |  external  |                         []                        |                     []                     |                  []                 |                          []                          |                                                      []                                                     |
|            unstake(uint256)           |  external  |                         []                        |                     []                     |                  []                 |                          []                          |                                                      []                                                     |
|                claim()                |  external  |                         []                        |                     []                     |                  []                 |                          []                          |                                                      []                                                     |
|                 exit()                |  external  |                         []                        |                     []                     |                  []                 |                          []                          |                                                      []                                                     |
|  constructor(address,address,uint256) |   public   |                         []                        |                     []                     | ['rewardsDuration', 'rewardsToken'] |                          []                          |                                                      []                                                     |
|                                       |            |                                                   |                                            |           ['stakingToken']          |                                                      |                                                                                                             |
|      setRewardsDuration(uint256)      |  external  |                   ['onlyOwner']                   |    ['periodFinish', 'block.timestamp']     |         ['rewardsDuration']         |        ['revert WaitToFinish()', 'onlyOwner']        |                                                      []                                                     |
|             stake(uint256)            |   public   | ['nonReentrant', 'whenNotPaused', 'updateReward'] |        ['balances', 'stakingToken']        |     ['balances', 'totalSupply']     |       ['revert ZeroAmount()', 'updateReward']        |                      ['stakingToken.safeTransferFrom(msg.sender,address(this),amount)']                     |
|                                       |            |                                                   |       ['totalSupply', 'msg.sender']        |                                     |          ['whenNotPaused', 'nonReentrant']           |                                                                                                             |
|                                       |            |                                                   |                  ['this']                  |                                     |                                                      |                                                                                                             |
|            unstake(uint256)           |   public   | ['nonReentrant', 'whenNotPaused', 'updateReward'] |        ['balances', 'stakingToken']        |     ['balances', 'totalSupply']     |          ['whenNotPaused', 'updateReward']           |                               ['stakingToken.safeTransfer(msg.sender,amount)']                              |
|                                       |            |                                                   |       ['totalSupply', 'msg.sender']        |                                     | ['revert NotEnoughBalance()', 'revert ZeroAmount()'] |                                                                                                             |
|                                       |            |                                                   |                                            |                                     |                   ['nonReentrant']                   |                                                                                                             |
|                claim()                |   public   | ['nonReentrant', 'whenNotPaused', 'updateReward'] |        ['rewards', 'rewardsToken']         |             ['rewards']             |          ['updateReward', 'whenNotPaused']           |                               ['rewardsToken.safeTransfer(msg.sender,reward)']                              |
|                                       |            |                                                   |               ['msg.sender']               |                                     |                   ['nonReentrant']                   |                                                                                                             |
|                 exit()                |   public   |                 ['whenNotPaused']                 |         ['balances', 'msg.sender']         |                  []                 |             ['whenNotPaused', 'unstake']             |                                                      []                                                     |
|                                       |            |                                                   |                                            |                                     |                      ['claim']                       |                                                                                                             |
|             fund(uint256)             |   public   |   ['onlyOwner', 'whenNotPaused', 'updateReward']  |       ['periodFinish', 'rewardRate']       |  ['lastUpdateTime', 'periodFinish'] |          ['updateReward', 'whenNotPaused']           | ['rewardsToken.balanceOf(address(this))', 'rewardsToken.safeTransferFrom(msg.sender,address(this),reward)'] |
|                                       |            |                                                   |    ['rewardsDuration', 'rewardsToken']     |            ['rewardRate']           |       ['onlyOwner', 'revert TooHighReward()']        |                                                                                                             |
|                                       |            |                                                   |     ['block.timestamp', 'msg.sender']      |                                     |                                                      |                                                                                                             |
|                                       |            |                                                   |                  ['this']                  |                                     |                                                      |                                                                                                             |
|     recoverERC20(address,uint256)     |  external  |                   ['onlyOwner']                   |              ['stakingToken']              |                  []                 |  ['revert FailedToWithdrawStaking()', 'onlyOwner']   |                          ['IERC20(tokenAddress).safeTransfer(owner(),tokenAmount)']                         |
|                                       |            |                                                   |                                            |                                     |                      ['owner']                       |                                                                                                             |
|      _lastTimeRewardApplicable()      |  internal  |                         []                        |    ['periodFinish', 'block.timestamp']     |                  []                 |                          []                          |                                                      []                                                     |
|           _rewardPerToken()           |  internal  |                         []                        | ['lastUpdateTime', 'rewardPerTokenStored'] |                  []                 |            ['_lastTimeRewardApplicable']             |                                                      []                                                     |
|                                       |            |                                                   |       ['rewardRate', 'totalSupply']        |                                     |                                                      |                                                                                                             |
|            _earned(address)           |  internal  |                         []                        |          ['balances', 'rewards']           |                  []                 |                 ['_rewardPerToken']                  |                                                      []                                                     |
|                                       |            |                                                   |         ['userRewardPerTokenPaid']         |                                     |                                                      |                                                                                                             |
|           balanceOf(address)          |  external  |                         []                        |                ['balances']                |                  []                 |                          []                          |                                                      []                                                     |
|       lastTimeRewardApplicable()      |  external  |                         []                        |                     []                     |                  []                 |            ['_lastTimeRewardApplicable']             |                                                      []                                                     |
|            rewardPerToken()           |  external  |                         []                        |                     []                     |                  []                 |                 ['_rewardPerToken']                  |                                                      []                                                     |
|            earned(address)            |  external  |                         []                        |                     []                     |                  []                 |                     ['_earned']                      |                                                      []                                                     |
|         getRewardForDuration()        |  external  |                         []                        |     ['rewardRate', 'rewardsDuration']      |                  []                 |                          []                          |                                                      []                                                     |
|     slitherConstructorVariables()     |  internal  |                         []                        |                     []                     |         ['rewardsDuration']         |                          []                          |                                                      []                                                     |
| slitherConstructorConstantVariables() |  internal  |                         []                        |                     []                     |     ['_ENTERED', '_NOT_ENTERED']    |                          []                          |                                                      []                                                     |
+---------------------------------------+------------+---------------------------------------------------+--------------------------------------------+-------------------------------------+------------------------------------------------------+-------------------------------------------------------------------------------------------------------------+

+-----------------------+------------+--------------------------+--------------------------------------------+-----------------------------------------------+----------------+
|       Modifiers       | Visibility |           Read           |                   Write                    |                 Internal Calls                | External Calls |
+-----------------------+------------+--------------------------+--------------------------------------------+-----------------------------------------------+----------------+
|     nonReentrant()    |  internal  |            []            |                     []                     | ['_nonReentrantBefore', '_nonReentrantAfter'] |       []       |
|    whenNotPaused()    |  internal  |            []            |                     []                     |             ['_requireNotPaused']             |       []       |
|      whenPaused()     |  internal  |            []            |                     []                     |               ['_requirePaused']              |       []       |
|      onlyOwner()      |  internal  |            []            |                     []                     |                ['_checkOwner']                |       []       |
| updateReward(address) |  internal  | ['rewardPerTokenStored'] | ['lastUpdateTime', 'rewardPerTokenStored'] |    ['_earned', '_lastTimeRewardApplicable']   |       []       |
|                       |            |                          |   ['rewards', 'userRewardPerTokenPaid']    |              ['_rewardPerToken']              |                |
+-----------------------+------------+--------------------------+--------------------------------------------+-----------------------------------------------+----------------+

## Variables and Auth

Contract IStakingRewards
+--------------------------+-------------------------+--------------------------+
|         Function         | State variables written | Conditions on msg.sender |
+--------------------------+-------------------------+--------------------------+
|        balanceOf         |            []           |            []            |
|          earned          |            []           |            []            |
|   getRewardForDuration   |            []           |            []            |
| lastTimeRewardApplicable |            []           |            []            |
|      rewardPerToken      |            []           |            []            |
|          stake           |            []           |            []            |
|         unstake          |            []           |            []            |
|          claim           |            []           |            []            |
|           exit           |            []           |            []            |
+--------------------------+-------------------------+--------------------------+

Contract StakingRewards
+-------------------------------------+-----------------------------------------------------------------------------------------------------------------------+-----------------------------------+
|               Function              |                                                State variables written                                                |      Conditions on msg.sender     |
+-------------------------------------+-----------------------------------------------------------------------------------------------------------------------+-----------------------------------+
|             constructor             |                                                      ['_status']                                                      |                 []                |
|         _nonReentrantBefore         |                                                      ['_status']                                                      |                 []                |
|          _nonReentrantAfter         |                                                      ['_status']                                                      |                 []                |
|             constructor             |                                                      ['_paused']                                                      |                 []                |
|                paused               |                                                           []                                                          |                 []                |
|          _requireNotPaused          |                                                           []                                                          |                 []                |
|            _requirePaused           |                                                           []                                                          |                 []                |
|                _pause               |                                                      ['_paused']                                                      |                 []                |
|               _unpause              |                                                      ['_paused']                                                      |                 []                |
|              _msgSender             |                                                           []                                                          |                 []                |
|               _msgData              |                                                           []                                                          |                 []                |
|             constructor             |                                                       ['_owner']                                                      |                 []                |
|                owner                |                                                           []                                                          |                 []                |
|             _checkOwner             |                                                           []                                                          |                 []                |
|          renounceOwnership          |                                                       ['_owner']                                                      |                 []                |
|          transferOwnership          |                                                       ['_owner']                                                      |                 []                |
|          _transferOwnership         |                                                       ['_owner']                                                      |                 []                |
|              balanceOf              |                                                           []                                                          |                 []                |
|                earned               |                                                           []                                                          |                 []                |
|         getRewardForDuration        |                                                           []                                                          |                 []                |
|       lastTimeRewardApplicable      |                                                           []                                                          |                 []                |
|            rewardPerToken           |                                                           []                                                          |                 []                |
|                stake                |                                                           []                                                          |                 []                |
|               unstake               |                                                           []                                                          |                 []                |
|                claim                |                                                           []                                                          |                 []                |
|                 exit                |                                                           []                                                          |                 []                |
|             constructor             |                                  ['stakingToken', 'rewardsToken', 'rewardsDuration']                                  |                 []                |
|          setRewardsDuration         |                                                  ['rewardsDuration']                                                  |                 []                |
|                stake                | ['rewards', 'lastUpdateTime', 'totalSupply', '_status', 'rewardPerTokenStored', 'balances', 'userRewardPerTokenPaid'] |                 []                |
|               unstake               | ['rewards', 'lastUpdateTime', 'totalSupply', '_status', 'rewardPerTokenStored', 'balances', 'userRewardPerTokenPaid'] | ['balances[msg.sender] < amount'] |
|                claim                |               ['rewards', 'lastUpdateTime', '_status', 'rewardPerTokenStored', 'userRewardPerTokenPaid']              |                 []                |
|                 exit                | ['rewards', 'lastUpdateTime', 'totalSupply', '_status', 'rewardPerTokenStored', 'balances', 'userRewardPerTokenPaid'] | ['balances[msg.sender] < amount'] |
|                 fund                |     ['rewards', 'lastUpdateTime', 'periodFinish', 'rewardPerTokenStored', 'rewardRate', 'userRewardPerTokenPaid']     |                 []                |
|             recoverERC20            |                                                           []                                                          |                 []                |
|      _lastTimeRewardApplicable      |                                                           []                                                          |                 []                |
|           _rewardPerToken           |                                                           []                                                          |                 []                |
|               _earned               |                                                           []                                                          |                 []                |
|              balanceOf              |                                                           []                                                          |                 []                |
|       lastTimeRewardApplicable      |                                                           []                                                          |                 []                |
|            rewardPerToken           |                                                           []                                                          |                 []                |
|                earned               |                                                           []                                                          |                 []                |
|         getRewardForDuration        |                                                           []                                                          |                 []                |
|     slitherConstructorVariables     |                                                  ['rewardsDuration']                                                  |                 []                |
| slitherConstructorConstantVariables |                                              ['_NOT_ENTERED', '_ENTERED']                                             |                 []                |
+-------------------------------------+-----------------------------------------------------------------------------------------------------------------------+-----------------------------------+