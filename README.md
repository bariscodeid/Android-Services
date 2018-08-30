# Android-Services
Kumpulan service android, seperti Toast, AlertDialog, SnackBar &amp; banyak lagi

### Service Toast Sederhana
Untuk menambahkan service ini kita hanya perlu mengimportkan library kedalam class

```.java
import android.widget.Toast;
```

kemudian mengeksekusi toast dengan event tertentu misalkan klik
```.java
btFacebook.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Toast.makeText(ToastActivity.this, "" + getString(R.string.url_facebook), 
                Toast.LENGTH_SHORT).show();
            }
});
```

dan berikut adalah tampilannya

<img src="https://github.com/bariscodeid/Android-Services/blob/master/screencapture/screenshot-1535618407604.jpg" heigt=300>
