# 🧪 Projeto de Testes Automatizados com **Java + Selenium + JUnit**

Este projeto demonstra como implementar testes automatizados utilizando **Selenium WebDriver**, **Java**, **JUnit** e o padrão de arquitetura **Page Object Model (POM)**.

O objetivo é oferecer uma estrutura clara, organizada e pronta para uso em aplicações reais, facilitando manutenção, escalabilidade e reutilização de código.


O exemplo utilizado é a automação da página do **Google**, realizando buscas e validando resultados.

---

## 📁 **Estrutura do Projeto**

```
AUTOMATIZADO
├── .vscode/
│
├── src/
│   └── test/
│       └── java/
│           └── automatizado/
│               ├── page/
│               │   ├── BasePO.java
│               │   └── GooglePO.java
│               │
│               ├── resource/
│               │   └── chromedriver.exe
│               │
│               └── teste/
│                   ├── BaseTest.java
│                   └── GoogleTest.java
│
├── target/
│
└── pom.xml
```

---

## 🧱 **Explicação das Pastas**

### **📁 page/** — *Page Objects (POO + POM)*

Contém classes que representam páginas reais do sistema.

* `BasePO.java`: classe mãe das páginas.
* `GooglePO.java`: representa a página do Google, incluindo métodos como `pesquisar()`.

Esse padrão torna os testes mais limpos e fáceis de manter.

---

### **📁 resource/**

Contém arquivos utilizados na automação.

* `chromedriver.exe`: driver necessário para o Selenium controlar o Chrome.

---

### **📁 teste/** — *Casos de Teste*

Contém os testes automatizados.

* `BaseTest.java`: inicializa o WebDriver, abre o navegador e define configurações.
* `GoogleTest.java`: contém os cenários de teste que utilizam os Page Objects.

---

## 🚀 **Como executar o projeto (passo a passo)**

### ✔️ **1. Instalar dependências obrigatórias**

* Java JDK 8+ instalado
* Maven instalado e configurado
* Google Chrome instalado
* ChromeDriver compatível com a versão do seu Chrome

### ✔️ **2. Clonar o repositório**

```
git clone https://github.com/Leandro-Pinheiro-Dev/Selenium-e-Java.git
```

### ✔️ **3. Importar o projeto na sua IDE**

Pode ser VSCode, IntelliJ IDEA ou Eclipse.

### ✔️ **4. Verificar o caminho do ChromeDriver**

O caminho configurado está em:

```
src/test/java/automatizado/resource/chromedriver.exe
```

Caso necessário, atualize a linha em `BaseTest.java`:

```
private static final String CAMINHO_DRIVER = "src/test/java/automatizado/resource/chromedriver.exe";
```

### ✔️ **5. Rodar os testes**

Você pode rodar:

* Pela IDE (run nos métodos com @Test), ou
* Via Maven:

```
mvn test
```

---

## 🔍 **Como funciona a execução**

1. `BaseTest` inicia o navegador.
2. O Google é carregado.
3. A classe `GooglePO` é instanciada.
4. O teste chama o método `pesquisar()`.
5. Um `WebDriverWait` aguarda o resultado aparecer.
6. O texto exibido é capturado.
7. O JUnit verifica se o resultado contém o esperado.

---

## 🧪 **Exemplo de Caso de Teste**

O teste realiza a busca "Batata Frita" e valida o resultado retornado pelo Google:

```java
@Test
public void TC001_deveSerPossivelPesquisarNoGoogleOTextoBatataFrita() {
    googlePage.pesquisar("Batata Frita");

    WebDriverWait wait = new WebDriverWait(driver, 50);
    wait.until(ExpectedConditions.visibilityOf(googlePage.divResultadoPesquisa));

    String resultado = googlePage.ObetrResultadoDaPesquisa();

    assertTrue(resultado.contains("Aproximadamente"));
}
```

---

## 🧩 Tecnologias utilizadas

* **Java 17+**
* **Selenium WebDriver**
* **JUnit 4**
* **Page Object Model (POM)**
* **ChromeDriver**
* **Maven**
