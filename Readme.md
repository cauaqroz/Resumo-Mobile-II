## Arquitetura da Plataforma Android
### 1. Visão Geral
O Android é uma pilha de softwares desenvolvida sobre o Kernel Linux, responsável pela abstração do hardware (memória, processador, dispositivos de entrada e saída). Essa estrutura segue o conceito de arquitetura em camadas, onde cada nível tem funções específicas.

### 2. Camadas da Arquitetura Android
- Kernel Linux
  - Responsável pelo gerenciamento de hardware.

  - Vantagens:
    - Segurança: herda a robustez do Linux.

    - Facilidade no desenvolvimento de drivers: sistema bem documentado e testado.

- Hardware Abstraction Layer (HAL)
  - Fornece interfaces padrão para acesso ao hardware.

> Exemplo: módulos específicos para câmera ou Bluetooth.

- Android Runtime (ART)
  - Executa arquivos DEX, otimizados para consumo mínimo de memória.

  - Suporta compilação AOT (Ahead-of-Time) e JIT (Just-in-Time), além de um sistema otimizado de coleta de lixo (Garbage Collection – GC).

- Bibliotecas Nativas (C/C++)

  - Componentes como ART e HAL utilizam código nativo.

  - Algumas bibliotecas podem ser acessadas via Java API, como o OpenGL ES para gráficos 2D e 3D.

  - O Android NDK permite uso direto de código C/C++.

- Java API Framework

  - Oferece APIs em Java para desenvolvimento de aplicativos Android.

  - Principais componentes:

> **Sistema de visualização (UI):** botões, listas, caixas de texto.

> **Gerenciador de recursos:** acesso a strings, gráficos e layouts.

> **Gerenciador de notificações:** alertas na barra de status.

> **Gerenciador de atividades:** controle do ciclo de vida dos apps.

> **Provedores de conteúdo:** permite compartilhamento de dados entre apps.

### Aplicativos do Sistema

- O Android inclui apps básicos como e-mail, SMS, navegador e calendário.

- Esses aplicativos não têm privilégios especiais e podem ser substituídos por apps de terceiros.

## Classe R.java
A classe R.java é gerada automaticamente pelo Android Studio e não deve ser alterada manualmente. Ela funciona como um mapeamento dos elementos da interface gráfica, permitindo a referência a imagens, textos, botões e outros componentes da aplicação.

### Principais Características:

Mapeia os elementos da pasta res/ para que possam ser acessados no código Java.

Contém identificadores públicos para acessar recursos, como:

- Imagens: R.drawable.icon

- Componentes de tela: R.id.botao, R.id.texto

- Arquivos: R.raw.musica, R.raw.video

- Strings: R.string.app_name, R.string.hello

> Importante:
A classe R.java é essencial para a organização e referência dos recursos da aplicação.

> Se houver erro nos arquivos da pasta res/, a classe pode não ser gerada corretamente, causando falhas no código.

> Não confundir com android.R, que pertence ao próprio sistema Android e não à aplicação.


## Método onCreate e Layout de uma Tela

O método onCreate() é fundamental para o funcionamento de uma Activity no Android. Ele define o layout da tela e permite a interação com os elementos da interface.

### Principais Conceitos:

- O layout é definido através do XML na pasta res/layout/ e carregado no código Java via setContentView().

- A classe R.java (gerada automaticamente) possibilita a referência aos elementos do XML no código Java.

- Para acessar componentes da interface, utilizamos findViewById() e associamos a um objeto correspondente.

> Exemplo:
``` Java 
EditText campoTexto = findViewById(R.id.meuEditText);
```

### Eventos na Interface Gráfica
- Eventos são ações disparadas pelos usuários (cliques, toques, teclas pressionadas etc.). Para lidar com eventos, utilizamos Listeners (Ouvintes), que podem ser configurados de três formas principais:

- No XML

  - Adicionando android:onClick="meuMetodo" diretamente no layout.

  - Com Classes Internas Anônimas

- Criando um Listener diretamente no código Java.

  - Com um Método Único

- Implementando uma interface Listener para capturar eventos de múltiplos componentes.

### Eventos Comuns:

- onClick() → Clique simples.

- onLongClick() → Clique longo (segurar pressionado).

- onFocusChange() → Ganha ou perde foco.

- onTouch() → Toque na tela, com ações diferenciadas como UP, DOWN e MOVE.

- onMenuItemClick() → Clique em um item de menu.

- onKey() → Pressionamento de teclas (físico ou virtual).

## ARQUIVO APK / AAB
#### APK (Android Package Kit):

Um arquivo compactado que contém todos os elementos necessários para instalar e executar um aplicativo Android em um dispositivo.
- Função: Distribuir e instalar aplicativos Android.

- Importância: Essencial para a instalação de aplicativos, sendo o formato tradicional para distribuição.

#### 2. AAB (Android App Bundle):

Um formato de publicação que inclui todo o código e recursos do aplicativo, mas a geração do APK final é feita pelo Google Play.
- Vantagens: Tamanho de download menor para o usuário, pois o Google Play entrega apenas os componentes necessários para o dispositivo. 

- Otimização para diferentes configurações de dispositivos.
Recursos dinâmicos, que podem ser baixados sob demanda.

- Motivo da adoção: Otimizar a distribuição de aplicativos, reduzir o tamanho dos downloads e melhorar a experiência do usuário.

#### 3. Diferenças entre APK e AAB:

- APK: 
  - Arquivo único para instalação.
  - Contém todos os recursos e código do aplicativo.
  - Tamanho de download fixo.
- AAB:
  - Formato de publicação, não de instalação direta.
  - Delega a geração do APK otimizado ao Google Play.
  - Tamanho de download variável, otimizado para cada dispositivo.

### 1. Processo de Assinatura:

- Importância: Garantir a autenticidade e integridade do aplicativo, verificando se ele não foi modificado por terceiros.

- Como é feita: Utilizando uma chave privada para assinar o aplicativo, gerando uma assinatura digital.

- Papel do Google: O Google Play exige que os aplicativos sejam assinados e oferece o Play App Signing, onde o Google gerencia a chave de assinatura, facilitando atualizações e protegendo contra perdas de chave.


### 5. Geração de APK e AAB:

> No Android Studio, você pode gerar um APK ou AAB através do menu "Build".

> Para gerar um APK, selecione "Build APK(s)".

> Para gerar um AAB, selecione "Build Bundle(s)".

> Em ambos os casos, o processo envolve a seleção da chave de assinatura e a configuração das opções de build.

## Programação Orientada a Objetos (POO):

- Conceitos fundamentais:
  - Classe: Um modelo ou molde para criar objetos.
  - Objeto: Uma instância de uma classe.
  - Mensagem: Uma requisição de um objeto para outro.
- Princípios da POO:
  - Herança: Uma classe pode herdar características de outra classe.
  - Encapsulamento: Agrupar dados e métodos dentro de uma classe, controlando o acesso.
  - Polimorfismo: Objetos de diferentes classes podem responder a uma mesma mensagem de maneiras diferentes.
  - Agregação e Composição: Relações entre classes que representam "todo-parte".
- Classes em Java/Kotlin:
  - Classes são definidas usando a palavra-chave class.
  - Atributos (estado) são declarados como variáveis dentro da classe.
  - Métodos (comportamento) são funções dentro da classe.
- Objetos em Java/Kotlin:
  - Objetos são criados a partir de classes usando a palavra-chave new.
- Exemplo de Classe Java:
```Java

public class Casa {
    String cor;

    public void abrirPorta() {
        // Código para abrir a porta
    }
}

// Instanciando um objeto da classe Casa
Casa minhaCasa = new Casa();
    minhaCasa.cor = "Azul";
    minhaCasa.abrirPorta();
//Getters e Setters:
//Métodos para acessar e modificar atributos privados de uma classe.
//Modificadores de Acesso:
//Controlam a visibilidade de atributos e métodos (ex: public, private, protected).

```

##  Telas e Resoluções

### Unidades de Medida:
- px (pixels): Evitar o uso, pois varia em diferentes dispositivos.
- dp ou dip (density-independent pixels): Unidade recomendada para garantir portabilidade.
- sp (scale-independent pixels): Recomendado para tamanhos de fonte.
- Densidade de Pixels (dpi): Número de pixels em uma área física da tela.
- Fornecer Bitmaps Alternativos:É importante fornecer diferentes versões de bitmaps para diferentes densidades de tela para evitar distorções.
  
- As densidades comuns são: **ldpi, mdpi, hdpi, xhdpi, xxhdpi, xxxhdpi**.
- A taxa de dimensionamento recomendada é **3:4:6:8:12:16** entre as densidades.

## View Elements - Button e Text

- TextView: Exibe texto na tela.
- O atributo android:text define o texto a ser exibido.
- EditText (PlainText):Permite que o usuário digite texto.
- O atributo android:hint exibe um texto de dica dentro do campo.
- O atributo android:inputType define o tipo de entrada (ex: texto, número, email).
- Button:
Um botão que pode ser clicado pelo usuário.
- O atributo android:onClick define o método a ser chamado quando o botão é clicado.
#### Exemplo de Código XML:

```XML

<TextView
    android:id="@+id/meuTextView"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Nome:"/>

<EditText
    android:id="@+id/meuEditText"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:hint="Digite seu nome"
    android:inputType="textPersonName"/>

<Button
    android:id="@+id/meuBotao"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Clique Aqui!"
    android:onClick="meuMetodo"/>
```
### Manipulando Eventos de Clique (Java/Kotlin):

- É necessário criar um método na Activity (ex: meuMetodo) para lidar com o clique do botão.
- Dentro desse método, você pode manipular outros elementos da UI (ex: alterar o texto de um TextView).

#### Exemplo de Código Java:
```Java

public void meuMetodo(View view) {
    TextView textoExibicao = findViewById(R.id.textoExibicao);
    textoExibicao.setText("Novo Texto!");
}

```

## View Elements - Imagens

- ImageView:É um elemento de UI para exibir imagens.
- Adicionando Imagens:
As imagens são adicionadas ao diretório res/drawable.
- No layout XML, usa-se a tag ImageView para exibir a imagem.
- O atributo android:src referencia a imagem no diretório drawable.
- Atributos da ImageView:
- layout_width e layout_height: Define o tamanho da ImageView.
- scaleType: Define como a imagem é dimensionada dentro da ImageView (ex: centerInside, fitStart, fitEnd, centerCrop).
#### Exemplo de Código XML:
```XML

<ImageView
    android:id="@+id/minhaImageView"
    android:layout_width="300dp"
    android:layout_height="300dp"
    android:src="@drawable/figura_saopaulo"
    android:scaleType="centerCrop"/>
```
## Activity e Ciclo de Vida - Ver1.pdf

- Activity:
Uma Activity é uma tela de interface do usuário em um aplicativo Android.
- É composta por uma classe Java/Kotlin (ex: MainActivity) e um arquivo XML (layout).
- Ciclo de Vida de uma Activity:
- A Activity passa por diferentes estados durante sua execução.
### Os principais estados e métodos são:
- onCreate(): Chamado quando a Activity é criada. Usado para inicialização.
- onStart(): A Activity se torna visível.
- onResume(): A Activity está em primeiro plano e interativa.
- onPause(): A Activity perde o foco (outra Activity está iniciando).
- onStop(): A Activity não está mais visível.
- onRestart(): A Activity é reiniciada após ser parcialmente oculta.
- onDestroy(): A Activity é destruída.
### Pilha de Activities:
- As Activities são organizadas em uma pilha.
- A nova Activity iniciada é colocada no topo da pilha.
