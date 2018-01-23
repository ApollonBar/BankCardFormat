# BankCardFormat

## 自动格式化银行卡号的EditText，每四位增加一个空格，并根据银行卡号判断该银行卡归属的银行及卡别

![image](https://github.com/smuyyh/BankCardFormat/blob/master/screenshot/device-1.png?raw=true)

### 使用
```
dependencies {
    compile 'com.yuyh.bankcardformat:library:1.0.3'
}
```
```xml
<com.example.library.BandCardEditText
    android:id="@+id/et"
    android:layout_width="match_parent"
    android:layout_height="30dp"
    android:text="622700187301032701"
    android:background="#cccccc"/>
```
```java
  tv = (TextView) findViewById(R.id.tv);
  editText = (BandCardEditText) findViewById(R.id.et);
  editText.setBankCardListener(new BankCardListener() {
      @Override
      public void success(String name) {
          tv.setText("所属银行：" + name);
      }
  
      @Override
      public void failure() {
          tv.setText("所属银行：");
      }
  });

  // 或者直接检测
  String carnum = "622700187301032701";
  if (BankCardUtils.checkBankCard(carnum)) {
      char[] ss = carnum.toCharArray();
      String bank = BankCardUtils.getNameOfBank(ss, 0);
  }
```



