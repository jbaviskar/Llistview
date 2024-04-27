package com.example.llistview;

import android.os.Bundle;
import android.view.View;
import android.widget.AdapterView;
import android.widget.ArrayAdapter;
import android.widget.ListView;
import android.widget.Toast;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

import java.util.ArrayList;

public class MainActivity extends AppCompatActivity {
ListView lv1;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_main);
        ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main), (v, insets) -> {
            Insets systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars());
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom);
            return insets;
        });

            lv1=findViewById(R.id.lv1);

        ArrayList<String> arr1=new ArrayList<>();
        arr1.add("praful");
        arr1.add("mayur");
        arr1.add("rushi");

        ArrayAdapter<String> arr2 =new ArrayAdapter<>(this, android.R.layout.simple_list_item_1,arr1);
        lv1.setAdapter(arr2);

        lv1.setOnItemClickListener(new AdapterView.OnItemClickListener() {
            @Override
            public void onItemClick(AdapterView<?> parent, View view, int position, long id) {
                if (position==0){
                    Toast.makeText(MainActivity.this, "clicked", Toast.LENGTH_SHORT).show();
                }
                else if ( position==1) {
                    Toast.makeText(MainActivity.this, "clicked on m", Toast.LENGTH_SHORT).show();

                }
                else {
                    Toast.makeText(MainActivity.this, "clicked on r", Toast.LENGTH_SHORT).show();
                }
            }
        });




    }
}
