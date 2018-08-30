# Android-Services
Kumpulan service android, seperti Toast, AlertDialog, SnackBar &amp; banyak lagi

### Service Toast Sederhana
Untuk menambahkan service ini kita hanya perlu mengimportkan library kedalam class

```.java
import android.widget.Toast;
```

kemudian mengeksekusi toast dengan event tertentu misalkan klik
```.java
Toast.makeText(ToastActivity.this, "" + getString(R.string.url_twitter), Toast.LENGTH_LONG).show();
```
