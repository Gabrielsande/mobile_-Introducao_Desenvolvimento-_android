# 📱 Exercícios — Eventos e Interação no Android

## 📚 Sobre o projeto

Este projeto reúne uma sequência de **6 exercícios práticos desenvolvidos na disciplina de Mobile**, com foco nos conceitos básicos de interação entre o usuário e a interface de um aplicativo Android.

Os exercícios trabalham principalmente:

- Eventos de clique utilizando `android:onClick`;
- Atualização de componentes da interface;
- Uso de `findViewById`;
- Alteração de textos com `setText`;
- Alteração da cor de textos;
- Geração de números aleatórios;
- Contadores;
- Exibição de mensagens no Logcat;
- Uso de condições `if/else`;
- Manipulação de componentes XML através do código Java.

---

# 🛠️ Tecnologias utilizadas

- **Java**
- **Android Studio**
- **Android SDK**
- **XML**
- **ConstraintLayout**

---

# 📂 Exercícios

## 1. 👋 Exercício 1 — Saudar

Neste exercício foi criado um botão **"Saudar"**, conectado à função `saudarUsuario()` através do atributo `android:onClick`.

Ao clicar no botão, o aplicativo:

1. Exibe uma mensagem no Logcat;
2. Localiza o `TextView` utilizando `findViewById`;
3. Atualiza o texto utilizando `setText`.

### Código Java

```java
public void saudarUsuario(View view) {
    System.out.println("Usuário clicou em Saudar!");

    TextView texto = findViewById(R.id.txtSaudacao);
    texto.setText("Olá, seja bem-vindo(a)!");
}
```

### Resultado

Ao clicar em **Saudar**, o aplicativo apresenta:

```text
Olá, seja bem-vindo(a)!
```

No Logcat:

```text
Usuário clicou em Saudar!
```

---

# 2. 🔢 Exercício 2 — Contador de Cliques

Neste exercício foi desenvolvido um contador que registra quantas vezes o botão **"Contar"** foi pressionado.

A variável `contador` é declarada fora da função para que seu valor seja mantido entre os diferentes cliques.

### Variável

```java
int contador = 0;
```

### Código Java

```java
public void contarClique(View view) {
    contador++;

    TextView texto = findViewById(R.id.txtContador);
    texto.setText("Cliques: " + contador);

    System.out.println("botão clicado " + contador + " vezes");
}
```

### Exemplo

Após três cliques:

```text
Cliques: 1
Cliques: 2
Cliques: 3
```

No Logcat:

```text
botão clicado 1 vezes
botão clicado 2 vezes
botão clicado 3 vezes
```

---

# 3. 🎲 Exercício 3 — Sorteio com Aviso no Logcat

Neste exercício o aplicativo gera aleatoriamente um número entre **0 e 10**.

O resultado é apresentado na tela e uma mensagem é enviada ao Logcat informando se o número sorteado é **par ou ímpar**.

### Código Java

```java
public void sortear(View view) {
    TextView textoResultado = findViewById(R.id.txtResultado);

    Random random = new Random();
    int numero = random.nextInt(11);

    textoResultado.setText("Resultado gerado: " + numero);

    if (numero % 2 == 0) {
        System.out.println("número par sorteado: " + numero);
    } else {
        System.out.println("número ímpar sorteado: " + numero);
    }
}
```

### Exemplo no Logcat

Número par:

```text
número par sorteado: 8
```

Número ímpar:

```text
número ímpar sorteado: 5
```

### Resultado na tela

```text
Resultado gerado: 8
```

O número sorteado sempre estará entre **0 e 10**.

---

# 4. 🎲 Exercício 4 — Dado com Histórico

Neste exercício a função `sortear()` foi modificada para `rolarDado()`.

O aplicativo simula o lançamento de um dado de seis lados.

A cada clique:

- Um número entre **1 e 6** é sorteado;
- O contador de rolagens é incrementado;
- A tela mostra o número da rolagem e o resultado;
- A informação também é registrada no Logcat.

### Variável

```java
int contador = 0;
```

### Código Java

```java
public void rolarDado(View view) {
    contador++;

    Random random = new Random();
    int numero = random.nextInt(6) + 1;

    TextView textoResultado = findViewById(R.id.txtResultado);

    textoResultado.setText(
            "Rolagem " + contador + ": resultado " + numero
    );

    System.out.println(
            "Rolagem " + contador + ": resultado " + numero
    );
}
```

### Exemplo na tela

```text
Rolagem 3: resultado 5
```

### Exemplo no Logcat

```text
Rolagem 1: resultado 2
Rolagem 2: resultado 6
Rolagem 3: resultado 5
```

O número sorteado sempre estará entre:

```text
1 e 6
```

---

# 5. 🔘 Exercício 5 — Dois Botões e uma Função em Comum

Neste exercício foram utilizados três botões, cada um com uma função diferente:

| Botão | Ação |
|---|---|
| **Aviso** | Exibe uma mensagem no Logcat |
| **Sortear** | Sorteia um número e mostra na tela |
| **Ambos** | Exibe a mensagem e realiza o sorteio |

## Função Aviso

A função `aviso()` apenas registra uma mensagem no Logcat.

```java
public void aviso(View view) {
    System.out.println("Botão Aviso clicado!");
}
```

## Função Sortear

A função `sortear()` gera um número aleatório entre **0 e 10** e exibe o resultado na tela.

```java
public void sortear(View view) {
    TextView textoResultado = findViewById(R.id.txtResultado);

    Random random = new Random();
    int numero = random.nextInt(11);

    textoResultado.setText("Resultado gerado: " + numero);
}
```

## Função Ambos

A função `avisarESortear()` executa as duas ações.

```java
public void avisarESortear(View view) {
    System.out.println("Botão Ambos clicado!");

    TextView textoResultado = findViewById(R.id.txtResultado);

    Random random = new Random();
    int numero = random.nextInt(11);

    textoResultado.setText("Resultado gerado: " + numero);
}
```

## XML dos botões

```xml
<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Aviso"
    android:onClick="aviso" />

<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Sortear"
    android:onClick="sortear" />

<Button
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Ambos"
    android:onClick="avisarESortear" />
```

O atributo:

```xml
android:onClick
```

é responsável por associar o botão a uma função existente na `Activity`.

---

# 6. 🎨 Exercício 6 — Cor conforme o Resultado

Neste exercício o aplicativo sorteia um número entre **0 e 10** e altera a cor do resultado dependendo se o número é **par ou ímpar**.

### Regras

- Número **par** → texto verde;
- Número **ímpar** → texto vermelho.

Além da alteração visual, o aplicativo registra no Logcat qual cor foi aplicada.

## Imports

```java
import android.graphics.Color;
import java.util.Random;
```

## Código Java

```java
public void sortear(View view) {
    TextView textoResultado = findViewById(R.id.txtResultado);

    Random random = new Random();
    int numero = random.nextInt(11);

    textoResultado.setText("Resultado gerado: " + numero);

    if (numero % 2 == 0) {
        textoResultado.setTextColor(
                Color.parseColor("#1F7A6C")
        );

        System.out.println(
                "Número par: " + numero + " — cor verde aplicada"
        );

    } else {
        textoResultado.setTextColor(
                Color.parseColor("#C62828")
        );

        System.out.println(
                "Número ímpar: " + numero + " — cor vermelha aplicada"
        );
    }
}
```

### Exemplo

Caso seja sorteado:

```text
8
```

O resultado será exibido em verde.

No Logcat:

```text
Número par: 8 — cor verde aplicada
```

Caso seja sorteado:

```text
5
```

O resultado será exibido em vermelho.

No Logcat:

```text
Número ímpar: 5 — cor vermelha aplicada
```

---

# 📌 Principais conceitos praticados

Durante os exercícios foram utilizados diversos conceitos fundamentais do desenvolvimento Android:

### Eventos de clique

```xml
android:onClick="nomeDaFuncao"
```

Permite executar uma função Java quando o usuário toca em um botão.

### Localização de componentes

```java
TextView texto = findViewById(R.id.txtResultado);
```

Permite acessar um componente definido no arquivo XML através do código Java.

### Alteração de texto

```java
texto.setText("Olá!");
```

Atualiza o conteúdo de um `TextView`.

### Alteração da cor

```java
texto.setTextColor(Color.parseColor("#1F7A6C"));
```

Modifica a cor do texto de um componente.

### Números aleatórios

```java
Random random = new Random();
int numero = random.nextInt(11);
```

Gera números aleatórios dentro do intervalo definido.

### Estruturas condicionais

```java
if (numero % 2 == 0) {
    // número par
} else {
    // número ímpar
}
```

Permite executar ações diferentes de acordo com o resultado.

### Logcat

```java
System.out.println("Mensagem");
```

Permite visualizar mensagens durante a execução do aplicativo através do Logcat do Android Studio.

---

# 🎯 Objetivo da atividade

A atividade teve como objetivo praticar os fundamentos da interação entre **interface XML e código Java** no desenvolvimento Android.

Por meio dos seis exercícios, foram trabalhados eventos de clique, manipulação de componentes, contadores, sorteios, estruturas condicionais, alteração visual e utilização do Logcat para acompanhar o funcionamento do aplicativo.

---

# 👨‍💻 Autor

**Gabriel Sandes**

Projeto desenvolvido para fins acadêmicos na disciplina de **Mobile**.
