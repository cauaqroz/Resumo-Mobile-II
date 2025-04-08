## Introdução ao Android
1. Qual é a arquitetura em camadas do Android? Descreva cada camada.
    > O android Possui 5 camadas sendo elas:
    >  - Kernel Linux: Gerencia o Hardware
    >  - HAL (camada de abstraçã): Padroniza acesso ao Hardware
    >  - Libs Nativa: Fornece Funcionalidas (ex.Graficas: OpenGL)
    >  - ART (runtime And.): Executa Apps Otimizados
    >  - Apps/Sistem: Interface e apps pré-instalados

2. Quais são as vantagens do Android ser um sistema de código aberto?
    > Permite personalização por fabricantes, ampla comunidade de desenvolvedores e acesso gratuito ao código-fonte.
3. Explique a função do Kernel Linux na plataforma Android.
    > Gerencia recursos de hardware como memória, processos e drivers, garantindo segurança e estabilidade.
4. Quais as principais diferenças entre as versões Android 10 e Android 11?
    > Android 11 trouxe: Modo escuro programável; Permissões temporárias para mic/câmera; Melhorias em notificações.
5. Como o Android Runtime (ART) otimiza o desempenho dos aplicativos?
    > Usa copilação AOT para converter bytecode para linguagem nativa acelerando a execução
## Componentes de Interface
1. Qual a diferença entre CheckBox e RadioButton?
    > CheckBox permite múltiplas seleções, enquanto RadioButton só permite uma seleção em um grupo.
2. Como você configuraria um RadioGroup para permitir apenas uma seleção?
   > Agrupe RadioButtons dentro de um RadioGroup no XML. O Android gerencia a seleção única automaticamente.
3. Explique o uso do atributo scaleType em uma ImageView.
    > Controla como a imagem se ajusta ao espaço. Ex.: centerCrop corta a imagem para preencher a view sem distorcer.
4. Para que serve o TextInputLayout e como ele melhora a experiência do usuário?
   >O TextInputLayout é um container que envolve um EditText, Melhora campos de texto com dicas flutuantes (hint) e validação de erros. 

5. Como vincular um método a um botão via XML usando android:onClick?
```XML
android:onClick="meuMetodo"  
```
## Ciclo de Vida da Activity
1. Liste os métodos do ciclo de vida de uma Activity e descreva quando cada um é chamado.

- `onCreate()`: Ao criar a Activity.  
- `onStart()`: Quando fica visível.  
- `onResume()`: Quando interativa.  
- `onPause()`: Ao perder foco (ex.: abrir outra Activity).  
- `onStop()`: Quando não está mais visível.  
- `onDestroy()`: Ao ser destruída. 

2. O que acontece se uma Activity é destruída (onDestroy()) e o usuário retorna a ela?
    > O Android recria a Activity chamando `onCreate()` novamente.

3. Qual a diferença entre onPause() e onStop()?
    > `onPause()` ocorre quando a Activity perde foco (ainda visível, como em notificações). `onStop()` quando é totalmente encoberta.

4. Como você salvaria o estado de uma Activity antes dela ser destruída?
    > Usando `onSaveInstanceState(Bundle)` para salvar dados e restaurar em `onCreate(Bundle)`.

5. O que é a pilha de Activities e como ela influencia a navegação?
    > É uma estrutura `LIFO` (último a entrar, primeiro a sair). Ao pressionar "Voltar", a Activity no topo é removida.

## Layouts e Responsividade

1. Por que usar dp e sp em vez de px em layouts Android?
    > Pois não é escalavel, um elemento de 100 px parecerá enorme em uma tela de 320 dpi e minúsculo em uma de 640 dpi.

2. Compare ConstraintLayout e LinearLayout. Quando usar cada um?
- `ConstraintLayout`: Para layouts complexos com vínculos entre elementos.  
- `LinearLayout`: Para alinhamentos simples em linha/coluna.
3. Como você centralizaria um Button vertical e horizontalmente em um ConstraintLayout?
    > No XML:  
```xml  
app:layout_constraintStart_toStartOf="parent"  
app:layout_constraintEnd_toEndOf="parent"  
app:layout_constraintTop_toTopOf="parent"  
app:layout_constraintBottom_toBottomOf="parent"  
```
4. Qual a função do atributo layout_weight no LinearLayout?
    > Distribui espaço proporcionalmente entre elementos. Ex.: Dois `Button`s com `layout_weight="1"` dividem o espaço igualmente.
5. Como adaptar um layout para diferentes orientações (retrato/paisagem)?
    > Criar pastas `res/layout-port` (retrato) e `res/layout-land` (paisagem) com XMLs específicos.
## Publicação e Distribuição
1. Qual a diferença entre APK e AAB?
- `APK`: Arquivo único para instalação.  
- `AAB`: Formato otimizado para a Play Store, gerando APKs específicos para cada dispositivo.
2. Por que é necessário assinar um APK antes da publicação?
    > Para verificar a autenticidade do desenvolvedor e evitar modificações não autorizadas.
3. Quais são os passos para publicar um aplicativo na Google Play Store?
-   1. Criar conta de desenvolvedor.  
-   2. Gerar APK/AAB assinado.  
-   3. Preencher metadados (descrição, imagens).  
-   4. Enviar para revisão.
4. O que é o arquivo keystore.jks e por que ele é importante?
    > Armazena chaves de assinatura do app. Perdê-lo impede atualizações do mesmo app na Play Store.
5. Como o Android App Bundle (AAB) reduz o tamanho do aplicativo?
    > Envia apenas recursos necessários para cada dispositivo (idioma, resolução, etc.)
## Prática e Projetos
1. Descreva como você implementaria um app de calculadora de gorjeta usando EditText e Button.
    > `EditText` para valor da conta.
    > `Button` para calcular.
    > Lógica no `onClick`

     ```Xml
        <EditText
        android:id="@+id/etBillAmount
        android:hint="Enter bill amount"
        android:inputType="numberDecimal"/>

        <Button
        android:id="@+id/btnCalculate"
        android:text="Calculate 10% Tip"/>

        <TextView
        android:id="@+id/tvTipResult"/>
    ```
    ```java 
    class MainActivity : AppCompatActivity() {
        private TextView result;
        private Button btnCal;
        private EditText valor;

        override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Initialize views
        etBillAmount = findViewById(R.id.etBillAmount)
        btnCalculate = findViewById(R.id.btnCalculate)
        tvTipResult = findViewById(R.id.tvTipResult)

        // Set onClick listener with arrow function
        btnCalculate.setOnClickListener {
            calculateTip()
        }
    }

    private fun calculateTip() {
        val billAmountText = etBillAmount.text.toString()
        
        if (billAmountText.isNotEmpty()) {
            val billAmount = billAmountText.toFloat()
            val tipAmount = billAmount * 0.1f  // 10% tip
            
            tvTipResult.text = "Tip amount: $${"%.2f".format(tipAmount)}"
        } else {
            tvTipResult.text = "Please enter a bill amount"
            }
        }
    }
   ```
2. Como passar dados entre Activities usando Intent? Demonstre com um exemplo.
- Enviar:  
  ```java  
  Intent intent = new Intent(this, SegundaActivity.class);

  intent.putExtra("chave", "valor");
  startActivity(intent);  
  ```
- Receber:
```java

String valor = getIntent().getStringExtra("chave");  
```
3. Qual a estrutura básica de um projeto Android no Android Studio?
    > - app/src/main/java/: Código-fonte.
    >  - app/src/main/res/: Recursos (layouts, imagens, strings).
    > - AndroidManifest.xml: Configuração do app.
4. Como você criaria um app com três Activities (tela inicial, formulário, confirmação)?
    > - Criar três classes (MainActivity, FormActivity, ConfirmaActivity)
    > - Definir os Layouts em Res/Layout
    > - Navegação com `Intent` e `StartActivity()`

5. Explique como usar CheckBox e RadioButton em um app de pedidos de pizza, conforme descrito na questão 05.
    > - `CheckBox`: Para Selecionar Multiplos Ingredientes ou codimentos
    > - `RadioButton`: Para Escolher Tamanhos, formas de retirar e pagamentos, em um `RadioGroup` 

## Questões Extra - possiveis pegadinhas

1. Para que serve o arquivo AndroidManifest.xml?
    > Ele declara `componentes` do app como `Activities`, `Services`, `permissões`, `tema padrão` e `informações essenciais` para o sistema Android.

2. Qual a diferença entre o `build.gradle (Project)` e o `build.gradle (Module: app)`?
    >  O primeiro configura o projeto inteiro (dependências globais, repositórios), enquanto o segundo configura apenas o módulo principal do app (dependências específicas, versionamento, etc.).

3. O que é a pasta `res/` e quais subpastas ela contém?
    >  Armazena recursos como layouts (layout/), imagens (drawable/), strings (values/), etc.


4. O que é uma `Activity` e qual sua função principal?
    > É uma tela do app, responsável pela interação com o usuário e exibição de interfaces.

5. Qual a diferença entre `TextView` e `EditText`?
    > `TextView` exibe `texto estático`, enquanto `EditText` permite `edição de texto` pelo usuário.

6. Para que serve o método `onCreate()` em uma Activity?
    > É chamado quando a Activity é criada, usado para inflar o layout e inicializar componentes.

7. Qual a diferença entre ConstraintLayout e LinearLayout?
    > `ConstraintLayout`: Posiciona elementos com base em constraints (vínculos) entre eles ou no layout pai.

    > `LinearLayout`: Organiza elementos em uma única linha (horizontal) ou coluna (vertical). 

8. Como definir o texto de um Button via XML e via código Java?

```XMl
XML:
android:text="Clique aqui"
```
```java
Java: 

button.setText("Clique aqui");
```

9. Como abrir uma segunda Activity a partir de um botão?
    > Resposta: Usando Intent:

``` java
java
btnConfimar.setOnClickListener(v-> {

Intent intent = new Intent(MainActivity.this, SegundaActivity.class);

startActivity(intent);  

});
```
10. O que é `findViewById()` e para que serve?
    > É usado para vincular elementos do XML (como Button) a variáveis no código, permitindo manipulá-los.