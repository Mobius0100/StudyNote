```bash
AT+CPING="www.taobao.com",1,4,64,1000,10000,255  // 测试ping淘宝
AT+CRESET     // 重启模块
AT&F      //初始化（只能恢复部分默认值）
ATZ     //初始化（只能恢复部分默认值）
AT+CFUN=0    //打开飞行模式
AT+CFUN=1	//关闭飞行模式
AT+GSN     //查询imei
AT+CIMI  //查询sim卡imsi
AT+CICCID      //读SIM卡CICCID
AT+CQCNV      //查询qcn版本
at+cpin?  	 //查询sim卡状态
at+cops?	//查询注册上的运营商名称
AT+CRESET  //复位
AT+CPOF  //关闭
at+simcomati  //查询模块版本
at+cnmp?	 //查询网络模式设置
at+cnmp=59   //强制TDS-CDMA only(移动3G)
at+cnmp=14  //强制WCDMA （联通3G）
at+cnmp=9  // 强制CDMA（电信3G）
at+cnmp=38  //强制LTE
at+cnmp=71     //强制5G SA
at+cnmp=109   //LTE+5G
at+cnmp=59  //强制2G+3G
AT+CNMP=55   //WCDMA+LTE+NR5G
AT+CNSMOD?  //查询当前网络模式
at+cpsi?	//查询注册状态
at+cgcontrdp      //查询ip地址
at+cautonet=0	 //关闭AP侧自动拨号
at+cautonet=1	//打开AP侧自动拨号
at+cgdcont?	   //查询APN设置
at+cgdcont=1,"IP","CTNET"	  //设置APN
AT+CGDCONT=1,"IPV6","CMNET"  //设置IPV6
at+cops=?	//扫描当前网络
AT+CUSBPIDSWITCH=9001,1,1  //设置9001模式(Windows)
AT+CUSBPIDSWITCH=9011,1,1  //设置9011模式(Linux)
at$qcrmcall=1,1		 //手动NDIS拨号
at$qcrmcall=0,1		//关闭NDIS拨号
AT+IPREX=9600      //固定波特率为9600
AT+CLVL=5                    //设置音量为5（最大）
At+cwiic=0x34,0x5a,0x3f,1   // 调整麦克风音量
0x3f代表最大增益35.25db， 最小为0x0,代表0db
调整ADC增益的指令为
At+cwiic=0x34,0x1e,0xff,1 //调整麦克风音量
0xff代表最大增益为0db，最小为0x00，代表-127db

```

