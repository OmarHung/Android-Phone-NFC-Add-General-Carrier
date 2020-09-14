# Android-Phone-NFC-Add-General-Carrier（此方法已無效）
使用具NFC功能之Android手機執行iCash2.0、悠遊卡、一卡通電子發票載具歸戶

前置作業：到Google Play下載「[NFC Reader](https://play.google.com/store/apps/details?id=com.ssaurel.nfcreader)  」
  
步驟一：到「[手機條碼-新增載具](https://www.einvoice.nat.gov.tw/APMEMBERVAN/GeneralCarrier/GeneralCarrierMgt!addGeneralCarrier)」頁面  
步驟二：選定「選取載具(卡片)類別」  
步驟三：選定「感應卡片」  
*若為iCash2.0請直接記住卡片上面的卡號，並跳過步驟四~六 
  
步驟四：使用手機打開「NFC Reader」APP   
步驟五：拿出卡片感應讀取內碼  
步驟六：記住ID(dex)後面的值，例如:ID(dex):123123，則請記住123123  
步驟七：打開瀏覽器的開發者工具並選擇Console分頁  
步驟八：在Console輸入以下代碼，注意cnum的值請設為步驟六取得的值，若卡片為iCash2.0請輸入卡號 
```javascript
var cnum = '123123';  //cnum的值請設為步驟六取得的值，若卡片為iCash2.0請輸入卡號
var cardCode = $('#ddlCardCode').val();
if(cardCode == '1H0001'){    
	if(!isNaN(cnum) && cnum>=0){     
		var cnum = cnum*1;     
		cnum = cnum.toString(16).toUpperCase();     
		while(cnum.length<8){     
			cnum = "0"+cnum;    
		}   
		cnum= cnum.substring(6,8)+cnum.substring(4,6)+cnum.substring(2,4)+cnum.substring(0,2);   
	}   
}   
componentCallBack(cnum); 
``` 
步驟九：按下Enter執行代碼   
步驟十：按下確認送出表單  
步驟十一：完成!!!
