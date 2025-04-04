### Questão 01
#### `ActivityMain.java`
```java

package com.wount.checklist_prova;

import android.os.Bundle;
import android.widget.Button;
import android.widget.CheckBox;
import android.widget.TextView;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

import kotlin.reflect.KFunction;

public class MainActivity extends AppCompatActivity {

// Declaração de variáveis para os CheckBoxes dos itens.
private CheckBox checkArroz, checkLeite, checkCarne, checkFeijao, checkRefri; 

// Declaração de variável para o botão.
private Button button; 

// Declaração de variável para exibir o resultado total.
private TextView totalResult; 

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this); // Habilita o modo Edge-to-Edge para a Activity.
        setContentView(R.layout.activity_main); // Define o layout da Activity.
        ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main), (v, insets) -> {
            Insets systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars());
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom); // Ajusta o padding para evitar sobreposição com as barras do sistema.
            return insets;
        });

        // Inicializa os CheckBoxes com os IDs definidos no layout.
        checkArroz = findViewById(R.id.checkArroz);
        checkLeite = findViewById(R.id.checkLeite);
        checkCarne = findViewById(R.id.checkCarne);
        checkFeijao = findViewById(R.id.checkFeijao);
        checkRefri = findViewById(R.id.checkRefri);

        // Inicializa o botão com o ID definido no layout.
        button = findViewById(R.id.button); 

        // Inicializa o TextView para exibir o resultado.
        totalResult = findViewById(R.id.totalResult);
        
        // Define o evento de clique no botão para chamar o método calcularTotal().
        button.setOnClickListener(v -> calcularTotal()); 
    }

    private void calcularTotal() {
        double total = 0.0; // Inicializa o total com 0.

        // Verifica se cada CheckBox está marcado e adiciona o valor correspondente ao total.
        if (checkArroz.isChecked()) total += 2.69;
        if (checkLeite.isChecked()) total += 2.70;
        if (checkCarne.isChecked()) total += 16.70;
        if (checkFeijao.isChecked()) total += 3.38;
        if (checkRefri.isChecked()) total += 3.00;

        // Formata o resultado como uma string e exibe no TextView.
        String resultado = "Total: R$ " + String.format("%.2f", total);
        totalResult.setText(resultado);
    }
}
```

#### `main_activity.xml`
```Xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/Title"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Lista De Compras"
        android:textSize="30dp"
        android:gravity="center"
        android:layout_marginBottom="20dp"/>

    <CheckBox
        android:id="@+id/checkArroz"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Arroz 1Kg R$2,69"
        android:textSize="20dp"/>

    <CheckBox
        android:id="@+id/checkLeite"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Leite Longa Vida R$2,70"
        android:textSize="20dp"/>

    <CheckBox
        android:id="@+id/checkCarne"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Carne Friboi R$16,70"
        android:textSize="20dp"/>

    <CheckBox
        android:id="@+id/checkFeijao"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Feijão Carioquinha 1Kg R$3,38"
        android:textSize="20dp"/>

    <CheckBox
        android:id="@+id/checkRefri"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Refrigerante Coca-Cola 2L R$3,00"
        android:textSize="20dp"/>

    <TextView
        android:id="@+id/totalResult"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Total:"
        android:layout_marginBottom="20dp"
        android:textSize="30dp"/>

    <Button
        android:id="@+id/button"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Finalizar"
        android:textSize="20dp"/>

</LinearLayout>
```


### Questão 2

```java
java


```