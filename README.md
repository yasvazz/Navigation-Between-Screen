<img width="1080" height="2400" alt="Screenshot_20260316_234018" src="https://github.com/user-attachments/assets/994b0647-c05d-48a9-9200-3d12d9ec4d4d" />
<img width="1080" height="2400" alt="Screenshot_20260316_234322" src="https://github.com/user-attachments/assets/09e9619a-f66c-4640-bac4-e74e770f8c0b" />
<img width="1080" height="2400" alt="Screenshot_20260316_234302" src="https://github.com/user-attachments/assets/34f768ae-6524-4f25-9b02-2aeda47ce490" />
<img width="1080" height="2400" alt="Screenshot_20260316_234236" src="https://github.com/user-attachments/assets/b5537436-a5e2-4c4a-9d9c-addfe0a6fdda" />



# Navigation Between Screens - Android

 Descrição do Projeto

Este projeto tem como objetivo demonstrar a navegação entre telas em um aplicativo Android utilizando *Navigation Compose*.

A aplicação simula um fluxo simples contendo:

* Tela de Login
* Tela de Menu
* Tela de Pedidos
* Tela de Perfil

A navegação é controlada por um **NavController**, definido na `MainActivity`, e repassado para cada tela juntamente com o `innerPadding`, seguindo boas práticas do Jetpack Compose.
 Tecnologias utilizadas

* Kotlin
* Jetpack Compose
* Navigation Compose

 Fluxo de navegação

Login → Menu → (Pedidos | Perfil)

# NOVOS COMMITS 



# 📱 Checkpoint 1 — Navigation com Jetpack Compose

## 🎯 Objetivo

Este projeto tem como objetivo evoluir uma aplicação Android já existente, aplicando conceitos de **navegação entre telas com Jetpack Compose**, com foco na **passagem de parâmetros**.

A proposta vai além de apenas implementar funcionalidades: busca demonstrar **entendimento do fluxo de navegação e da comunicação entre telas**.

---

## 🧠 Conceitos Aplicados

Durante o desenvolvimento foram aplicados os seguintes conceitos:

* Navegação com `NavHost` e `NavController`
* Definição de rotas dinâmicas
* Passagem de parâmetros obrigatórios
* Passagem de parâmetros opcionais (query parameters)
* Uso de múltiplos parâmetros
* Tipagem de argumentos com `NavType`
* Recuperação de dados via `arguments`

---

## 🚀 Evoluções Implementadas

### 🔹 1. Parâmetro Obrigatório — Tela de Perfil

A navegação foi configurada para exigir um parâmetro obrigatório (`nome`) ao acessar a tela de perfil.

### ✔ Implementação:

* Definição da rota dinâmica:

```kotlin id="a1"
"perfil/{nome}"
```

* Envio do parâmetro:

```kotlin id="a2"
navController.navigate("perfil/Fulano de Tal")
```

* Recuperação do valor:

```kotlin id="a3"
val nome = it.arguments?.getString("nome", "Usuário Genérico")
```

* Exibição na interface:

```kotlin id="a4"
text = "PERFIL - $nome"
```

📌 **Importante:**
O uso de parâmetros obrigatórios garante que a tela receba sempre os dados necessários para funcionar corretamente.

---

### 🔹 2. Parâmetro Opcional — Tela de Pedidos

Foi implementado um parâmetro opcional (`cliente`), permitindo que a tela funcione com ou sem valor informado.

### ✔ Implementação:

* Definição da rota com query:

```kotlin id="b1"
"pedidos?cliente={cliente}"
```

* Definição de valor padrão:

```kotlin id="b2"
navArgument("cliente") {
    defaultValue = "Cliente Genérico"
}
```

* Envio do parâmetro:

```kotlin id="b3"
navController.navigate("pedidos?cliente=Cliente XPTO")
```

* Recuperação:

```kotlin id="b4"
it.arguments?.getString("cliente")
```

* Exibição:

```kotlin id="b5"
text = "PEDIDOS - $cliente"
```

📌 **Importante:**
Parâmetros opcionais aumentam a flexibilidade da navegação, evitando erros quando um valor não é informado.

---

### 🔹 3. Uso de Valor Padrão

Quando nenhum valor é enviado para o parâmetro opcional, o sistema utiliza automaticamente o valor definido como padrão.

📌 Isso garante:

* Robustez na navegação
* Melhor experiência do usuário
* Menor chance de falhas

---

### 🔹 4. Múltiplos Parâmetros — Perfil (nome + idade)

A navegação foi evoluída para suportar múltiplos parâmetros simultaneamente.

### ✔ Implementação:

* Definição da rota:

```kotlin id="c1"
"perfil/{nome}/{idade}"
```

* Tipagem dos argumentos:

```kotlin id="c2"
navArgument("nome") { type = NavType.StringType }
navArgument("idade") { type = NavType.IntType }
```

* Envio:

```kotlin id="c3"
navController.navigate("perfil/Fulano de Tal/27")
```

* Recuperação:

```kotlin id="c4"
val nome = it.arguments?.getString("nome")
val idade = it.arguments?.getInt("idade", 0)
```

* Exibição:

```kotlin id="c5"
text = "PERFIL - $nome tem $idade anos"
```

📌 **Importante:**
A tipagem com `NavType` garante segurança e evita erros de conversão de dados.

---

## ⚙️ Estrutura da Navegação

A navegação do aplicativo foi estruturada da seguinte forma:

* `NavHost`: define o grafo de navegação
* `NavController`: gerencia as transições entre telas
* `composable`: define cada rota
* `navArgument`: define e tipa os parâmetros

---

## 🔄 Fluxo de Navegação

1. O usuário interage com um botão
2. A navegação é disparada com `navController.navigate()`
3. Os parâmetros são enviados pela rota
4. A tela de destino recupera os dados via `arguments`
5. Os valores são utilizados na interface

---

## 📂 Estrutura do Projeto

```
📦 navigation
 ┣ 📂 screens
 ┃ ┣ LoginScreen.kt
 ┃ ┣ MenuScreen.kt
 ┃ ┣ PerfilScreen.kt
 ┃ ┗ PedidosScreen.kt
 ┣ MainActivity.kt
```

---

## 🧪 Boas Práticas Aplicadas

* Código organizado por responsabilidades (screens separadas)
* Uso de parâmetros tipados
* Definição de valores padrão
* Evolução incremental do projeto
* Commits representando cada etapa da implementação

---

## 📊 Resultado

O projeto demonstra:

✔ Domínio da navegação com Jetpack Compose
✔ Capacidade de manipular dados entre telas
✔ Implementação correta de parâmetros obrigatórios e opcionais
✔ Uso de múltiplos parâmetros com tipagem segura

---

## 🏁 Conclusão

Este projeto evidencia não apenas a implementação funcional da navegação, mas também a compreensão de:

* Como os dados trafegam entre telas
* Como estruturar rotas dinâmicas
* Como garantir segurança e flexibilidade na navegação

Mais do que fazer funcionar, foi possível compreender **como e por que cada parte do sistema funciona**.

---

## 🔗 Repositório

👉 (adicione aqui o link do seu GitHub)
