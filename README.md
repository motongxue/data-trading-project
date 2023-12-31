# data-trading-project
本仓库是存放了数据交易项目的部分内容，并进行了脱密处理。
1. 关于分片传输和断点续传降低传输失败的风险、文件妙传的功能实现，可见仓库：![https://github.com/motongxue/ConcurrentTransferKit](https://github.com/motongxue/ConcurrentTransferKit)
2. 关于大数据量的MySQL数据并发导出CSV格式，可见仓库：![https://github.com/motongxue/MySQL2CSV](https://github.com/motongxue/MySQL2CSV)

## ConcurrentTransferKit
**概述**
本项目旨在提供高效且可靠的文件传输解决方案，从多个角度考虑了文件传输的不同方面，包括分片传输、断点续传和文件秒传 。这些功能的实现可以提供更好的用户体验、带宽利用率和数据完整性。
**功能特点**
- 分片传输：我们允许用户将大文件分成小块（分片）进行传输，以降低传输失败的风险。
- 断点续传：当传输过程中出现网络中断或者其他原因导致传输失败时，我们可以从上次传输失败的分片开始重新传输，而不需要重新传输整个文件。
- 文件秒传：当用户传输的文件已经存在于服务器上时，我们可以直接跳过传输过程，从而节省时间和带宽。
- 并发传输：我们可以利用goroutine实现并发，同时传输多个文件，从而提高带宽利用率和传输效率。
- 文件合并：防止服务器宕机导致的文件合并失败，我们可以在文件合并过程中使用redis的互斥锁，从而保证文件合并的原子性。

## MySQL2CSV
**概述**
MySQL2CSV 是一个开源工具，旨在帮助用户将 MySQL 数据库中的数据以并发方式导出成 CSV 格式的文件。它支持字段选择，具有并发性能优化，可以有效地降低导出时间，并支持批量操作。
**功能特点**
- 并发导出：利用 Go 语言的并发特性，可以同时处理多个数据块，提高导出性能。
- 字段选择：允许用户选择要导出的特定字段，以满足个性化需求。
- 批量操作：支持批量导出多个表或查询结果，提高效率。
- 高性能：通过并发和优化的方法，显著降低导出数据所需的时间。
- 易于使用：简单的配置和命令行界面使得项目易于使用和集成。
