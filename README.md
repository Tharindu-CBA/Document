## Payable Android SDK

### Add the SDK to Your Project

### Implement Single Payment

- make sure the following permissions are present:
````
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
````
- Implement the  ``PayableCallBack`` interface and the ``PayableCardReaderCallBack`` interface in your **Actvity** class.   
````
public class EnterSwipeSales_Activity extends AppCompatActivity implements PayableCallBack,PayableCardReaderCallBack {
````
- Next, we'll assume that you're going to launch the scanner from a button, and that you've set the button's onClick handler in the layout XML via ``android:onClick="onSale"``. Then, add the method as:
````
private void onSale(View v){
       //here we hard coded the values for amount 
       //and invoice nuber as 5.00 and 100
        try {
            payable.sale(this,this,5.00,100);
        } catch (PayableException e) {
            // TODO: handle the exception
        }
    }
````
- Finally , Override ``onSuccessSales(TxSaleRes txSaleRes)``, ``onFailureSales(PayableException e)`` Methods.
  (If payament is success it will be called onSuccessSales method, otherwise it will be onFailerSales)
  ````
   @Override
    public void onSuccessSales(TxSaleRes txSaleRes) {
        Toast.makeText(this,"Success Sale",Toast.LENGTH_SHORT);
    }

    @Override
    public void onFailureSales(PayableException e) {
        Toast.makeText(this,"Failere Sale",Toast.LENGTH_SHORT);
    }
    ````
  
