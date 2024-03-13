学习cpp-httplib项目，总结经验：
  1. std::thread、std::unique_lock<std::mutex>、std::conditional_variable 对象的联合使用，避免多线程竞争问题。
       std::conditional_variable 条件变量类 wait(std::unique_lock<std::mutex>)，阻止线程；notify_one()，唤醒线程
  2. C++代码风格在实际工程项目中尽量简单、易懂，能少用复杂的lambda表达式尽量少用。
  3. cpp-httplib项目本身固有的问题：
       工作线程在一个任务中接收客户机请求数据，没有设置接收缓冲区多次接收，可能会导致请求包数据不全。
       同样，在发送数据时，一次未必能发送成功或者完毕，也应该设置发送缓冲区。
