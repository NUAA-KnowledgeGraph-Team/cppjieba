1. 已经修改test/unittest/unicode_test.cpp,include的头文件增加了<ctime>
2. 已经build
    1. windows下是通过codeblocks的mingw及make来完成的
    2. 因此需要加`codeblocks_install_path\bin`添加到系统的环境变量PATH中，其中`codeblocks_install_path`是你的codeblocks的安装目录。`codeblocks_install_path\bin`目录下有gcc,g++,mingw32-make等exe文件。
    3. mingw32-make可以理解为win下的make,cmd可以通过doskey命令设置make为mingw32-make的别名，powershell可以通过set alias设置别名，不多赘述。
3. 测试样例demo
   1. `./test/demo.cpp`文件中有demo.cpp(这个文件包含了main函数入口)，演示了接口的使用。
   2. 这个生成的可执行文件在当前目录(即`./`)，做了多次设置的调整，总是有些exe的生成的地方不对，如果这个的位置正确了另一个就错了。因此我选择放弃配置，生成demo.exe之后手动复制到`./test/`目录下。
   3. 在`./test/`目录下运行demo.exe即可看到样例运行结果如下。
        ```
        他来到了网易杭研大厦
        [demo] Cut With HMM
        他/来到/了/网易/杭研/大厦
        [demo] Cut Without HMM
        他/来到/了/网易/杭/研/大厦
        我来到北京清华大学
        [demo] CutAll
        我/来到/北京/清华/清华大学/华大/大学
        小明硕士毕业于中国科学院计算所，后在日本京都大学深造
        [demo] CutForSearch
        小明/硕士/毕业/于/中国/科学/学院/科学院/中国科学院/计算/计算所/，/后/在/日本/京都/大学/日本京都大学/深造
        [demo] Insert User Word
        男默/女泪
        男默女泪
        [demo] CutForSearch Word With Offset
        [{"word": "小明", "offset": 0}, {"word": "硕士", "offset": 6}, {"word": "毕业", "offset": 12}, {"word": "于", "offset": 18}, {"word": "中国", "offset": 21}, {"word": "科学", "offset": 27}, {"word": "学院", "offset": 30}, {"word": "科学院", "offset": 27}, {"word": "中国科学院", "offset": 21}, {"word": "计算", "offset": 36}, {"word": "计算所", "offset": 36}, {"word": "，", "offset": 45}, {"word": "后", "offset": 48}, {"word": "在", "offset": 51}, {"word": "日本", "offset": 54}, {"word": "京都", "offset": 60}, {"word": "大学", "offset": 66}, {"word": "日本京都大学", "offset": 54}, {"word": "深造", "offset": 72}]
        [demo] Lookup Tag for Single Token
        [拖拉机:n, CEO:eng, 123:m, 。:x]
        [demo] Tagging
        我是拖拉机学院手扶拖拉机专业的。不用多久，我就会升职加薪，当上CEO，走上人生巅峰。
        [我:r, 是:v, 拖拉机:n, 学院:n, 手扶拖拉机:n, 专业:n, 的:uj, 。:x, 不用:v, 多久:m, ，:x, 我:r, 就:d, 会:v, 升职:v, 加薪:nr, ，:x, 当上:t, CEO:eng, ，:x, 走上:v, 人生:n, 巅峰:n, 。:x]
        [demo] Keyword Extraction
        我是拖拉机学院手扶拖拉机专业的。不用多久，我就会升职加薪，当上CEO，走上人生巅峰。
        [{"word": "CEO", "offset": [93], "weight": 11.7392}, {"word": "升职", "offset": [72], "weight": 10.8562}, {"word": "加薪", "offset": [78], "weight": 10.6426}, {"word": "手扶拖拉机", "offset": [21], "weight": 10.0089}, {"word": "巅峰", "offset": [111], "weight": 9.49396}]
        ```
    4. 从测试结果可以大略看出一些词性的标记是什么。例如代词是用r标记，名词是用n标记。最好弄一份详细的词性标记表，其实总共也没多少种词性。
date：2019年1月22日