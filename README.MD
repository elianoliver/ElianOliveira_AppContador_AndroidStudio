### Resumo

Esse código em `SobreActivity.java` basicamente pega o valor do contador enviado pela `MainActivity` e o exibe em um elemento de texto na tela da `SobreActivity`. Isso permite que o usuário veja o valor do contador quando navega para a segunda atividade.

![[img.jpg|center|500]]

### MainActivity.java

### **1. Pacote e Importações:**

```java
package com.example.firstapp;

import androidx.appcompat.app.AppCompatActivity;  // Importa funcionalidades para atividades no Android
import android.content.Intent;  // Importa classes para manipular intent
import android.os.Bundle;  // Importa classes para lidar com o ciclo de vida da atividade
import android.view.View;  // Importa a classe View para interação com a interface do usuário
import android.widget.Button;  // Importa a classe Button para trabalhar com botões
import android.widget.TextView;  // Importa a classe TextView para trabalhar com textos
```

Aqui, estamos indicando ao Android Studio quais bibliotecas e funcionalidades da plataforma Android vamos usar no nosso código.

### **2. Declaração da Classe MainActivity:**

```java
public class MainActivity extends AppCompatActivity {

```

`MainActivity` é a tela principal da nossa aplicação. Estendemos `AppCompatActivity` para obter recursos modernos de atividades no Android.

### **3. Atributos da Classe:**

```java
    private Integer contador = 0;  // Armazena o valor do contador
    private TextView txtContador;  // Referência ao elemento de texto na interface
    private Button btMais;  // Referência ao botão de adição
    private Button btMenos;  // Referência ao botão de subtração
    private Button btnSobre;  // Referência ao botão que abre a atividade Sobre

```

`contador`: Guarda o valor do contador.

`txtContador`: Aponta para o elemento de texto na tela que mostrará o contador.

`btMais`, `btMenos`, `btnSobre`: Referências aos botões de adição, subtração e abertura da atividade Sobre.

### **4. Método `onCreate`:**

```java
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);  // Define o layout da atividade

        // Associa os elementos do layout aos objetos Java
        txtContador = findViewById(R.id.textContador);
        btMais = findViewById(R.id.buttonMais);
        btMenos = findViewById(R.id.buttonMenos);
        btnSobre = findViewById(R.id.buttonSobre);

        txtContador.setText(String.valueOf(this.getContador()));  // Define o valor inicial do contador na tela
    }

```

`onCreate`: Método chamado quando a tela é criada.

`setContentView(R.layout.activity_main)`: Define qual arquivo de layout será usado para esta atividade.

`findViewById`: Liga os elementos do layout aos objetos Java.

`txtContador.setText(String.valueOf(this.getContador()))`: Inicializa o texto do contador na tela com o valor atual.

### **5. Métodos de Ação:**

```java
    public Integer getContador(){
        return this.contador;
    }

    public void adicionar(View view){
        this.contador++;  // Incrementa o contador
        txtContador.setText(String.valueOf(this.getContador()));  // Atualiza o texto na tela
    }

    public void subtrair(View view){
        this.contador--;  // Decrementa o contador
        txtContador.setText(String.valueOf(this.getContador()));  // Atualiza o texto na tela
    }

    public void abreSobre(View view){
        Intent i = new Intent(MainActivity.this, SobreActivity.class);  // Cria uma intenção para abrir a SobreActivity
        i.putExtra("contador", this.getContador());  // Passa o valor do contador para a SobreActivity
        startActivity(i);  // Inicia a atividade Sobre
    }

```

`getContador()`: Retorna o valor atual do contador.

`adicionar(View view)`: Incrementa o contador e atualiza a exibição.

`subtrair(View view)`: Decrementa o contador e atualiza a exibição.

`abreSobre(View view)`: Abre a atividade Sobre, passando o valor atual do contador.

Espero que agora esteja mais claro! Se tiver mais dúvidas ou precisar de mais esclarecimentos, sinta-se à vontade para perguntar.

### SobreActivity.java

### 1. **Pacote e Importações:**

```java
// Importações necessárias para a classe SobreActivity
package com.example.firstapp;
import androidx.appcompat.app.AppCompatActivity;
import android.content.Intent;
import android.os.Bundle;
import android.widget.TextView;

```

### 2. **Declaração da Classe SobreActivity:**

```java
// Classe que representa a segunda atividade (SobreActivity)
public class SobreActivity extends AppCompatActivity {

```

### 3. **Atributos da Classe:**

```java
// Componentes visuais da atividade
private TextView txtContador; // Para exibir o valor do contador
private Integer contador; // Para armazenar o valor do contador recebido da MainActivity

```

### 4. **Método `onCreate`:**

```java
@Override
protected void onCreate(Bundle savedInstanceState) {
    // Método chamado quando a atividade é criada
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_sobre); // Define o layout associado a esta atividade

    // Obtém a intenção que iniciou a atividade
    Intent intent = getIntent();

    // Extrai o valor do contador da intenção, com 0 como valor padrão
    this.contador = intent.getIntExtra("contador", 0);

    // Associa o TextView do layout ao objeto Java
    txtContador = findViewById(R.id.textContadorSobre);

    // Define o texto do TextView com o valor do contador convertido para string
    txtContador.setText(String.valueOf(this.contador));
}

```

O método `onCreate` é como a "porta de entrada" da atividade quando ela é iniciada.

`Intent` é um objeto que transporta dados entre atividades. Aqui, estamos obtendo a intenção que iniciou a `SobreActivity`.

`getIntExtra("contador", 0)`: Extrai o valor inteiro associado à chave "contador" da intenção. Se não houver valor, é utilizado 0 como padrão.

`findViewById(R.id.textContadorSobre)`: Obtém a referência ao elemento de texto no layout da `SobreActivity`.

`setText(String.valueOf(this.contador))`: Define o texto do TextView com o valor do contador convertido para string.
