# Rust常用的量化交易库
在 Rust 生态中，量化交易相关的库正在逐步发展，以下是一些常用的库和工具，涵盖数据处理、回测、交易接口和策略开发等方面：

以下是整理后的表格形式，包含 Python 库、对应的 Rust 替代方案及相关教程链接（部分为示例链接，实际需替换为有效资源）：

---

| Python 库       | Rust 替代方案   | 库的作用（功能场景）                     | 教程/资源链接                              |
|-----------------|----------------|----------------------------------------|-------------------------------------------|
| `numpy`         | `ndarray`      | **多维数组计算**（矩阵运算、数学函数）       | [Rust ndarray 官方文档](https://docs.rs/ndarray/latest/ndarray/) ｜
| `pandas`        | `Polars`       | **数据处理与分析**（DataFrame、时间序列）    | [Polars 用户指南](https://pola-rs.github.io/polars-book/user-guide/) |
| `scikit-learn`  | `Linfa`        | **机器学习算法**（分类、回归、聚类等）       | [Linfa GitHub 示例](https://github.com/rust-ml/linfa) |
| `matplotlib`    | `plotters`     | **数据可视化**（折线图、柱状图等）           | [Plotters 示例库](https://github.com/38/plotters-rs) |
| `pytorch`       | `tch-rs`       | **深度学习**（张量计算、神经网络训练）       | [tch-rs 教程](https://github.com/LaurentMazare/tch-rs) |
| `networkx`      | `petgraph`     | **图论与网络分析**（路径查找、拓扑排序）     | [Petgraph 文档](https://docs.rs/petgraph/latest/petgraph/) |

---

### **关键场景扩展**
1. **量化交易常用组合**  
   - 数据预处理：`Polars` + `ndarray`  
   - 策略回测：`Polars`（数据处理） + `ta-rs`（技术指标）  
   - 可视化：`plotters` 绘制收益曲线/K线图  

2. **性能敏感场景**  
   - Rust 的 `ndarray` 和 `Polars` 在**高频数据处理**中比 Python 有显著性能优势。  

3. **机器学习全流程**  
   - `Linfa`（传统机器学习） → `tch-rs`（深度学习） → `plotters`（结果可视化） 
---

以下是 Rust 生态中常用的量化交易相关库，以表格形式整理，包含库名、主要功能和官方文档链接：

---

| **库名**         | **功能**                                                                 | **官方文档/资源链接**                                                                 |
|------------------|-------------------------------------------------------------------------|-------------------------------------------------------------------------------------|
| **ndarray**      | 多维数组计算库（类似 NumPy），支持矩阵运算和数学操作                          | [ndarray 文档](https://docs.rs/ndarray/latest/ndarray/) ｜
| **Polars**       | 高性能 DataFrame 库（类似 Pandas），用于数据处理、时间序列分析                | [Polars 官方文档](https://pola-rs.github.io/polars-book/user-guide/)                |
| **ta-rs**        | 技术分析指标库（MACD、RSI、布林带等）                                       | [ta-rs GitHub](https://github.com/soulmachine/ta-rs)                                |
| **Backtest-rs**  | 轻量级回测框架，支持多资产策略测试                                           | [Backtest-rs GitHub](https://github.com/psymbio/backtest-rs)                       |
| **CCXT-RS**      | 加密货币交易所统一 API 封装（支持 Binance、Coinbase 等）                     | [CCXT-RS GitHub](https://github.com/ccxt-rust/ccxt-rs)                             |
| **Taqos**        | 事件驱动的回测引擎，适合高频交易策略                                          | [Taqos GitHub](https://github.com/taqos/taqos)                                     |
| **Linfa**        | 机器学习库（类似 scikit-learn），支持回归、分类等传统算法                      | [Linfa GitHub](https://github.com/rust-ml/linfa)                                   |
| **tch-rs**       | PyTorch 的 Rust 绑定，用于深度学习策略开发                                   | [tch-rs GitHub](https://github.com/LaurentMazare/tch-rs)                           |
| **Plotters**     | 数据可视化库（类似matplotlib，绘制K线图、收益曲线等）                                        | [Plotters GitHub](https://github.com/38/plotters-rs)                               |
| **Tokio**        | 异步运行时库，用于构建低延迟交易系统和实时数据流处理                           | [Tokio 官方文档](https://tokio.rs/)                                                |
| **Tungstenite**  | WebSocket 客户端库，用于接收交易所实时行情数据                               | [Tungstenite GitHub](https://github.com/snapview/tungstenite-rs)                   |
| **Candle**       | Hugging Face 推出的轻量级深度学习框架，适合量化场景                          | [Candle GitHub](https://github.com/huggingface/candle)                             |
| **Statrs**       | 统计计算库（概率分布、假设检验等）                                           | [Statrs GitHub](https://github.com/boxtown/statrs)                                 |
| **Petgraph**     | 图论分析库（用于投资组合优化、网络分析等）                                    | [Petgraph 文档](https://docs.rs/petgraph/latest/petgraph/)                         |

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
