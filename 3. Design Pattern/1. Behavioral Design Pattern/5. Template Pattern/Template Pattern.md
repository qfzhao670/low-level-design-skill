Problem Statement
Imagine you're building a system that reads data from different file types like CSV, XML, and JSON. Every file reader needs to follow the same basic process: open the file, read the content, and close the file.
If you don't use the Template Method Pattern, you'll end up writing the same opening and closing logic over and over again in each file reader class.

