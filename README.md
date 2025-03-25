# Rust常用的量化交易库
在 Rust 生态中，量化交易相关的库正在逐步发展，以下是一些常用的库和工具，涵盖数据处理、回测、交易接口和策略开发等方面：

以下是整理后的表格形式，包含 Python 库、对应的 Rust 替代方案及相关教程链接（部分为示例链接，实际需替换为有效资源）：

---

| **Rust库**         | **Python库** | **功能**                                                                 | **官方文档/资源链接**                                                                 |
|------------------|------------------|-------------------------------------------------------------------------|-------------------------------------------------------------------------------------|
| **ndarray**      | `numpy`          | 多维数组计算库，支持矩阵运算和数学操作                          | [ndarray 文档](https://docs.rs/ndarray/latest/ndarray/)                            |
| **Polars**       | `pandas`         | 高性能 DataFrame 库，用于数据处理、时间序列分析                | [Polars 官方文档](https://pola-rs.github.io/polars-book/user-guide/)                |
| **ta-rs**        | `TA-Lib`         | 技术分析指标库（MACD、RSI、布林带等）                                       | [ta-rs GitHub](https://github.com/soulmachine/ta-rs)                                |
| **Backtest-rs**  | `Backtrader`     | 轻量级回测框架，支持多资产策略测试                                           | [Backtest-rs GitHub](https://github.com/psymbio/backtest-rs)                       |
| **CCXT-RS**      | `CCXT`           | 加密货币交易所统一 API 封装（支持 Binance、Coinbase 等）                     | [CCXT-RS GitHub](https://github.com/ccxt-rust/ccxt-rs)                             |
| **Taqos**        | `Zipline`        | 事件驱动的回测引擎，适合高频交易策略                                          | [Taqos GitHub](https://github.com/taqos/taqos)                                     |
| **Linfa**        | `scikit-learn`   | 机器学习库，支持回归、分类等传统算法                      | [Linfa GitHub](https://github.com/rust-ml/linfa)                                   |
| **tch-rs**       | `PyTorch`        | PyTorch 的 Rust 绑定，用于深度学习策略开发                                   | [tch-rs GitHub](https://github.com/LaurentMazare/tch-rs)                           |
| **Plotters**     | `matplotlib`     | 数据可视化库（绘制K线图、收益曲线等）                                        | [Plotters GitHub](https://github.com/38/plotters-rs)                               |
| **Candle**       | `PyTorch`        | 轻量级深度学习框架，适合量化场景                                             | [Candle GitHub](https://github.com/huggingface/candle)                             |
| **Tokio**        | `asyncio`        | 异步运行时库，用于构建低延迟交易系统和实时数据流处理                           | [Tokio 官方文档](https://tokio.rs/)                                                |
| **Tungstenite**  | `websockets`     | WebSocket 客户端库，用于接收交易所实时行情数据                               | [Tungstenite GitHub](https://github.com/snapview/tungstenite-rs)                   |
| **Statrs**       | `scipy.stats`    | 统计计算库（概率分布、假设检验等）                                           | [Statrs GitHub](https://github.com/boxtown/statrs)                                 |
| **Petgraph**     | `networkx`       | 图论分析库（用于投资组合优化、网络分析等）                                    | [Petgraph 文档](https://docs.rs/petgraph/latest/petgraph/)                         |

---

### **关键说明**
1. **功能对应关系**  
   - Rust 的 `ta-rs` 对标 Python 的 `TA-Lib`（但后者是 C 库的 Python 封装）。  
   - `Tokio` 是 Rust 的异步运行时，对标 Python 的 `asyncio`，但性能更强。  

2. **无直接对应的库**  
   - `Backtest-rs` 和 `Taqos` 是 Rust 原生回测框架，Python 生态类似工具有 `Backtrader` 和 `Zipline`，但设计理念不同。  

3. **深度学习差异**  
   - `tch-rs` 和 `Candle` 均依赖 PyTorch 生态，但 `Candle` 更轻量级。  

---

### **分类说明**
1. **核心工具**  
   - 数据处理：`Polars`、`ndarray`  
   - 技术指标：`ta-rs`  
   - 回测框架：`Backtest-rs`、`Taqos`  

2. **交易接口**  
   - 加密货币：`CCXT-RS`  
   - 传统经纪商：需封装 IBKR/盈透证券等 API（社区实现）  

3. **机器学习**  
   - 传统算法：`Linfa`  
   - 深度学习：`tch-rs`、`Candle`  

4. **可视化与辅助**  
   - 绘图：`Plotters`  
   - 统计：`Statrs`  
   - 异步运行时：`Tokio`  

---

### **高频交易场景推荐组合**
```text
1. 数据获取: Tungstenite (WebSocket) + CCXT-RS (REST API)  
2. 数据处理: Polars + ndarray  
3. 策略逻辑: ta-rs (技术指标) + 自定义 Rust 代码  
4. 回测: Backtest-rs  
5. 部署: Tokio (异步运行时)  
```



---
