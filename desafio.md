ATIVIDADE:

Com base no projeto das "telas" (Activity) demonstrado das 3 "telas" e o projeto do IMC.

Crie um novo projeto onde o usuário precisa clicar no botão "Calcular IMC" para chama a tela para entrar com os parâmetros (peso e altura).

Ao clicar em Calcular, dependendo da classificação do IMC, abre uma nova Activity com o valor do peso, altura e IMC e traga uma mensagem positiva para a classificação.

Todas as telas devem ter o botão de fechar (ou um ícone) no qual retorna para tela principal.


```java
//Arquivo UnderWeight - Abaixo do Peso

package com.example.preguiça;

import android.os.Bundle;
import android.util.Log;
import android.view.View;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;

public class UnderweightActivity extends AppCompatActivity {
    private static final String TAG = "UnderweightActivity";

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_underweight);
        Log.d(TAG, "onCreate chamado");
        // onCreate: Chamado quando a Activity é criada. Use para inicializar componentes.

        double imc = getIntent().getDoubleExtra("IMC", 0);
        TextView tvResultado = findViewById(R.id.tvResultado);
        tvResultado.setText(String.format("IMC: %.2f\nClassificação: Abaixo do peso", imc));
    }

    public void finish(View view) {
        finish();
    }

    @Override
    protected void onStart() {
        super.onStart();
        Log.d(TAG, "onStart chamado");
        // onStart: Chamado quando a Activity se torna visível para o usuário.
    }

    @Override
    protected void onResume() {
        super.onResume();
        Log.d(TAG, "onResume chamado");
        // onResume: Chamado quando a Activity está em primeiro plano e interativa.
    }

    @Override
    protected void onPause() {
        super.onPause();
        Log.d(TAG, "onPause chamado");
        // onPause: Chamado quando a Activity perde o foco (outra Activity está iniciando).
    }

    @Override
    protected void onStop() {
        super.onStop();
        Log.d(TAG, "onStop chamado");
        // onStop: Chamado quando a Activity não está mais visível.
    }

    @Override
    protected void onRestart() {
        super.onRestart();
        Log.d(TAG, "onRestart chamado");
        // onRestart: Chamado quando a Activity é reiniciada após ser parcialmente oculta.
    }

    @Override
    protected void onDestroy() {
        super.onDestroy();
        Log.d(TAG, "onDestroy chamado");
        // onDestroy: Chamado quando a Activity é destruída.
    }
}
```

```java
//Arquivo Input - Colocar Informações Peso e Altura
package com.wount.apphome;

import android.content.Intent;
import android.os.Bundle;
import android.util.Log;
import android.view.View;
import android.widget.EditText;
import android.widget.Toast;
import androidx.appcompat.app.AppCompatActivity;

public class InputActivity extends AppCompatActivity {
    private static final String TAG = "InputActivity";

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_input);
        Log.d(TAG, "onCreate chamado");

        EditText etPeso = findViewById(R.id.etPeso);
        EditText etAltura = findViewById(R.id.etAltura);

        findViewById(R.id.btnCalcular).setOnClickListener(v -> {
            try {
                double peso = Double.parseDouble(etPeso.getText().toString());
                double altura = Double.parseDouble(etAltura.getText().toString());
                double imc = peso / (altura * altura);

                Intent intent;
                if (imc < 18.5) {
                    intent = new Intent(InputActivity.this, UnderweightActivity.class);
                } else if (imc < 24.9) {
                    intent = new Intent(InputActivity.this, NormalWeightActivity.class);
                } else {
                    intent = new Intent(InputActivity.this, OverweightActivity.class);
                }

                intent.putExtra("IMC", imc);
                startActivity(intent);
            } catch (NumberFormatException e) {
                Toast.makeText(InputActivity.this, "Por favor, insira valores válidos.", Toast.LENGTH_SHORT).show();
            }
        });

        findViewById(R.id.btnFechar).setOnClickListener(v -> finish());
    }

    @Override
    protected void onStart() {
        super.onStart();
        Log.d(TAG, "onStart chamado");
    }

    @Override
    protected void onResume() {
        super.onResume();
        Log.d(TAG, "onResume chamado");
    }

    @Override
    protected void onPause() {
        super.onPause();
        Log.d(TAG, "onPause chamado");
    }

    @Override
    protected void onStop() {
        super.onStop();
        Log.d(TAG, "onStop chamado");
    }

    @Override
    protected void onRestart() {
        super.onRestart();
        Log.d(TAG, "onRestart chamado");
    }

    @Override
    protected void onDestroy() {
        super.onDestroy();
        Log.d(TAG, "onDestroy chamado");
    }
}
```