1. Introdução ao Android
O que é Android?

Sistema operacional móvel baseado em Linux, desenvolvido pela Open Handset Alliance (OHA).

Código aberto (AOSP), permitindo personalização por fabricantes.

Dominância no mercado (80% dos dispositivos móveis).

Versões do Android

Nomenclatura baseada em doces (ex: KitKat, Lollipop, Oreo).

Principais recursos:

Android 10: Modo escuro, melhorias em privacidade.

Android 11: Gravação de tela nativa, permissões temporárias.

Android 12: Material You (design dinâmico), Painel de Privacidade.

Arquitetura do Android

Camadas:

Linux Kernel: Gerencia hardware (memória, processador).

HAL (Hardware Abstraction Layer): Interface para drivers.

Android Runtime (ART): Executa bytecode DEX (substituiu a Dalvik VM).

Bibliotecas Nativas (C/C++): OpenGL, SQLite.

Java API Framework: Fornece classes para desenvolvimento (Activity, View).

Aplicativos do Sistema: Apps pré-instalados (Gmail, Play Store).

2. Arquivos APK e AAB
APK (Android Package Kit)

Pacote de instalação tradicional.

Contém código, recursos e certificado de assinatura.

Exemplo: app-debug.apk gerado pelo Android Studio.

AAB (Android App Bundle)

Formato moderno (obrigatório na Play Store desde 2021).

Vantagens:

Redução de tamanho (15% menor que APK universal).

Geração dinâmica de APKs otimizados para cada dispositivo (ABI, densidade de tela, idioma).

Estrutura:

Módulo base (base/).

Módulos de recursos (feature1/, asset_pack/).

Assinatura Digital

Necessária para instalação/atualização.

Chave privada deve ser guardada (perda = novo app na Play Store).

3. Classe R.java e Método onCreate
Classe R.java

Gerada automaticamente pelo Android Studio.

Mapeia recursos (IDs) declarados em res/ (layouts, strings, imagens).

Exemplo:

java
Copy
TextView tv = findViewById(R.id.textView1); // Acessa um TextView pelo ID.
Método onCreate

Ponto de entrada de uma Activity.

Configura layout e inicializa componentes.

Exemplo:

java
Copy
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main); // Define o layout.
    Button btn = findViewById(R.id.button);
    btn.setOnClickListener(v -> { /* Lógica do clique */ });
}
4. Tratamento de Eventos
Formas de Implementar:

XML (atributo android:onClick):

xml
Copy
<Button android:onClick="calcularSoma" />
Run HTML
java
Copy
public void calcularSoma(View v) { /* Lógica */ }
Classe Anônima:

java
Copy
button.setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View v) { /* Lógica */ }
});
Implementar Interface (OnClickListener):

java
Copy
public class MainActivity extends AppCompatActivity implements View.OnClickListener {
    @Override
    public void onClick(View v) {
        if (v.getId() == R.id.button) { /* Lógica */ }
    }
}
Tipos de Eventos:

onClick, onLongClick, onTouch, onKey.

5. POO em Android
Conceitos Básicos:

Classe: Modelo para objetos (ex: class Pessoa).

Objeto: Instância de uma classe (ex: Pessoa p1 = new Pessoa()).

Encapsulamento: Uso de private + getters/setters.

java
Copy
private String nome;
public String getNome() { return nome; }
public void setNome(String nome) { this.nome = nome; }
Herança:

Reutilização de código (ex: class Cachorro extends Animal).

super: Chama métodos da classe pai.

java
Copy
@Override
public void dormir() {
    super.dormir(); // Chama o método da classe Animal.
    Log.d("Cachorro", "Ronca...");
}
Polimorfismo:

Sobrescrita de métodos (@Override).

Modificadores de Acesso:

public, private, protected, default.

6. Dicas para a Prova
Prática:

Criar um projeto com APK/AAB.

Implementar eventos em botões.

Usar findViewById e a classe R.java.

Teoria:

Diferenças entre APK e AAB.

Ciclo de vida de uma Activity (onCreate, onResume).

Princípios de POO (herança, encapsulamento).

Exemplo Prático (POO + Eventos):

java
Copy
// Classe Animal (superclasse)
public class Animal {
    protected String nome;
    public void emitirSom() { Log.d("Animal", "Som genérico"); }
}

// Classe Cachorro (subclasse)
public class Cachorro extends Animal {
    @Override
    public void emitirSom() { Log.d("Cachorro", "Au Au!"); }
}

// Uso em MainActivity
Animal meuPet = new Cachorro();
meuPet.emitirSom(); // Saída: "Au Au!"
Referência Rápida:

APK: Universal, maior tamanho.

AAB: Otimizado, menor tamanho.

onCreate: Inicializa Activity.

R.java: Ponte entre XML e Java.

POO: Encapsulamento, herança, polimorfismo.


