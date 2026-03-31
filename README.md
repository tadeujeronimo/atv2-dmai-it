# DeliveryApp - Atividade 2 (DMAI)

Aplicativo Android nativo desenvolvido na Atividade 2 do curso Desenvolvimento Mobile Android Intermediário (iTalents).

O projeto simula um fluxo de delivery com autenticação, listagem de produtos, carrinho, favoritos, pedidos e gerenciamento de usuários/produtos.

## Objetivo da atividade

- Melhoria do layout da feature de Favoritos (Favorite).

## Funcionalidades

- Login de usuário com token JWT.
- Cadastro de cliente.
- Listagem de produtos.
- Cadastro, edição e remoção de produtos.
- Marcação de produtos favoritos (persistência local).
- Carrinho de compras com atualização de itens.
- Finalização de pedido e histórico de pedidos.
- Cadastro e seleção de endereços (persistência local).
- Listagem e gerenciamento de usuários.

## Arquitetura e padrões

- Kotlin + Android Views (ViewBinding e DataBinding).
- MVVM com `ViewModel` e `LiveData`.
- Repositories para orquestrar fontes locais e remotas.
- Injeção de dependência com Hilt.
- Persistência local com Room.
- Comunicação HTTP com Retrofit + OkHttp + Gson.

## Tecnologias

- Android SDK 35 (minSdk 29).
- Kotlin 2.0.21.
- Gradle 8.7.3 (AGP).
- Hilt 2.52.
- Room 2.6.1.
- Retrofit 2.11.0.
- OkHttp 4.12.0.

## Estrutura resumida

```text
app/src/main/java/com/tadeujeronimo/deliveryapp
|- data
|  |- local        # Room (database, dao, entities)
|  |- remote       # data sources remotos
|  |- repositories # regra de acesso a dados
|  |- service      # interfaces Retrofit
|  |- util         # SharedPreferences, interceptor, converters
|- di              # módulos Hilt
|- ui              # Activities, adapters, menu, interfaces
|- DeliveryApplication.kt
```

## Pre-requisitos

- Android Studio (recomendado: versão recente com suporte ao AGP 8.7+).
- JDK 11.
- Gradle Wrapper (já incluído no repositório).
- API backend rodando em rede local.

## Configuração da API

Atualmente a base URL está fixa em:

```kotlin
http://10.0.2.2:3000/
```

Arquivo:

```text
app/src/main/java/com/tadeujeronimo/deliveryapp/di/ApiModule.kt
```

Se necessário, ajuste para o IP da máquina que está executando o backend.

## Como executar

1. Clone o repositório.
2. Abra no Android Studio.
3. Aguarde o sync do Gradle.
4. Configure a URL da API (se necessário).
5. Execute em emulador ou dispositivo físico.

### Via terminal

```bash
./gradlew assembleDebug
./gradlew installDebug
```

Para executar testes:

```bash
./gradlew test
./gradlew connectedAndroidTest
```

## Fluxo básico do app

1. Usuário autentica em `LoginActivity`.
2. App salva token em `SharedPreferences`.
3. `AuthInterceptor` injeta o token no header `Authorization`.
4. Usuário navega por produtos, favoritos, carrinho e pedidos.
5. Endereços, favoritos e pedidos locais são persistidos via Room.

## Permissões Android

- `android.permission.INTERNET`
- `android.permission.ACCESS_NETWORK_STATE`

## Licença

[GNU](LICENSE)
