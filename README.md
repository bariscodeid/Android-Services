# Android-Services
Kumpulan service android, seperti Toast, AlertDialog, SnackBar &amp; banyak lagi

### Bagian 1: Toast
Untuk menambahkan service ini kita hanya perlu `mengimportkan library` kedalam class

```.java
import android.widget.Toast;
```

kemudian mengeksekusi `toast` dengan `event` tertentu misalkan klik
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

<img src="https://github.com/bariscodeid/Android-Services/blob/master/screencapture/screenshot-1535618407604.jpg" width='320'>

Done.

### Bagian 2: Snackbar
Untuk menambahkan `snackbar` pada aplikasi kita, kita perlu menambahkan beberapa sourcecode dan config dasarnya yaitu 
- Layout RootView harus `CoordiantorLayout` & `Memiliki ID`
- Menambahkan `Dependency Libarary Design` pada `build.gradle (Module: app)`
<br>

<b>Pertama</b> kita tambahkan `library dependency` terlebih dahulu kedalam `build.gradle (Module: app)`
```.build.gradle
implementation 'com.android.support:design:26.1.0'
```

<b>Kedua</b> kita tambahkan terlebih dahulu layout dasarnya seperti dibawah ini dengan sebuah tombol untuk melakukan aksinya

```.xml
<?xml version="1.0" encoding="utf-8"?>
<android.support.design.widget.CoordinatorLayout xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:id="@+id/clLayoutWidget"
    tools:context=".ToastActivity">
    
    <RelativeLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent">
        
        <Button
            android:layout_marginTop="30dp"
            android:layout_centerHorizontal="true"
            android:layout_below="@+id/ivPhotoProfile"
            android:id="@+id/btnFb"
            android:drawableLeft="@drawable/facebook"
            android:layout_width="300dp"
            android:layout_height="60dp"
            android:textAllCaps="false"
            android:textSize="20sp"
            android:text="Akun Facebook"/>
            
    </RelativeLayout>
</android.support.design.widget.CoordinatorLayout>
```

<b>Ketiga</b> Deklarasikan View

```.java
package dev.id.bariscode.project2mengenallayoutwidget;

import android.annotation.SuppressLint;
import android.graphics.Color;
import android.support.design.widget.CoordinatorLayout;
import android.support.design.widget.Snackbar;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.Gravity;
import android.view.View;
import android.widget.Button;
import android.widget.RelativeLayout;
import android.widget.TextView;
import android.widget.Toast;

public class ToastActivity extends AppCompatActivity {

    //TODO 1: Deklarasikan View / Widget Button
    Button btFacebook;
    CoordinatorLayout coordinatorLayout;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_toast);

        //TODO 2: Inisialisasi (Memberikan Nilai) View / Widget Button
        btFacebook = (Button)findViewById(R.id.btnFb);
        btTwitter = (Button)findViewById(R.id.btnTw);
        btWebsite = (Button)findViewById(R.id.btnBl);
        btAbout = (Button)findViewById(R.id.btnAb);

        coordinatorLayout = (CoordinatorLayout)findViewById(R.id.clLayoutWidget) ;

        //TODO 3: Memberikan Event (Action) untuk Button
        btFacebook.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Toast.makeText(ToastActivity.this, "" + getString(R.string.url_facebook), 
                Toast.LENGTH_SHORT).show();
                Snackbar popUp = Snackbar
                        .make(coordinatorLayout, "" + getString(R.string.url_facebook) + "", 
                        Snackbar.LENGTH_LONG)
                        .setAction("SHOW", new View.OnClickListener() {
                            @Override
                            public void onClick(View view) {
                                Snackbar popupDele = Snackbar
                                .make(coordinatorLayout, "Message is deleted!", 
                                Snackbar.LENGTH_SHORT);
                                popupDele.show();
                            }
                        });
                popUp.show();
            }
        });
    }
}
```

Dan berikut adalah hasil dari popup Snackbar diatas

<img src="https://github.com/bariscodeid/Android-Services/blob/master/screencapture/screenshot-1535619988261.jpg" width='320'>&nbsp;
<img src="https://github.com/bariscodeid/Android-Services/blob/master/screencapture/screenshot-1535620001030.jpg" width='320'>

Done

### Bagian 3: AlertDialog
Alert dialog bisa kita custom dan mengeksekusinya yaitu kita perlu menambahkan builder kedalam sistem untuk menampilkan alert dialog terlebut, berikut adalah schema dari alert dialog

<img src="https://github.com/bariscodeid/Android-Services/blob/master/screencapture/alert-dialog.png">

<b>Pertama</b> `Deklarasikan & Inisialisasi Class AlertDialog.Builder` terlebih dahulu didalam `OnCreate` Method

```.java
final AlertDialog.Builder builder = new AlertDialog.Builder(this);
```

jika sudah selanjutnya buat alert dialognya

```.java
btFacebook.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
            builder
               .setMessage(getString(R.string.url_facebook))
               .setTitle("Informasi")
               .setPositiveButton("POSITIVE", new DialogInterface.OnClickListener() {
                   @Override
                   public void onClick(DialogInterface dialogInterface, int i) {
                       Toast.makeText(ToastActivity.this, "This POSITIVE button!", Toast.LENGTH_SHORT).show();
                   }
                })
                
                .setNegativeButton("NEGATIVE", new DialogInterface.OnClickListener() {
                    @Override
                    public void onClick(DialogInterface dialogInterface, int i) {
                        Toast.makeText(ToastActivity.this, "This NEGATIVE button!", Toast.LENGTH_SHORT).show();
                    }
                 });
                 AlertDialog dialog = builder.create();
                 dialog.show();
            }
});
```

Jika sudah berikut adalah hasil dari execute program alert dialog

<img src="https://github.com/bariscodeid/Android-Services/blob/master/screencapture/screenshot-1535620585302.jpg" width='320'>&nbsp;
<img src="https://github.com/bariscodeid/Android-Services/blob/master/screencapture/screenshot-1535620600997.jpg" width='320'>

Untuk menambahkan Icon dalam Alert dialog berikut kita tambahkan pada setIcon seperti dibawah ini

```.java
builder
    .setMessage(getString(R.string.url_facebook))
    .setTitle("Informasi")
    .setIcon(R.mipmap.ic_launcher)
    .setPositiveButton("POSITIVE", new DialogInterface.OnClickListener() {
        @Override
        public void onClick(DialogInterface dialogInterface, int i) {
            Toast.makeText(ToastActivity.this, "This POSITIVE button!", Toast.LENGTH_SHORT).show();
        }
     })
     .setNegativeButton("NEGATIVE", new DialogInterface.OnClickListener() {
         @Override
         public void onClick(DialogInterface dialogInterface, int i) {
            Toast.makeText(ToastActivity.this, "This NEGATIVE button!", Toast.LENGTH_SHORT).show();
         }
      });
      AlertDialog dialog = builder.create();
      dialog.show();
```
