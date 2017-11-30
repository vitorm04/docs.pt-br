---
title: "Comando dotnet – CLI do .NET Core"
description: "Saiba mais sobre o comando dotnet (o driver genérico para as ferramentas da CLI do .NET Core) e seu uso."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: bba8d77cda7538bf008dc0f510f9279d3c695c3d
ms.sourcegitcommit: a19548e5167cbe7e9e58df4ffd8c3b23f17d5c7a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2017
---
# <a name="dotnet-command"></a>Comando dotnet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nome

`dotnet` – Driver geral para executar os comandos da linha de comando.

## <a name="synopsis"></a>Sinopse

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbose] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [-v|--verbose] [--version]
```
---

## <a name="description"></a>Descrição

`dotnet` é um driver genérico para a cadeia de ferramentas da CLI (Interface de Linha de Comando). Invocado por conta própria, ele fornece breve instruções de uso.

Cada recurso específico é implementado como um comando. Para usar o recurso, o comando é especificado após `dotnet`, como [`dotnet build`](dotnet-build.md). Todos os argumentos após o comando são seus próprios argumentos.

A única vez que `dotnet` é usado como um comando em si é ao executar [aplicativos dependentes da estrutura](../deploying/index.md). Especifique uma DLL de aplicativo após o verbo `dotnet` para executar o aplicativo (por exemplo, `dotnet myapp.dll`).

## <a name="options"></a>Opções

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

`--additionaldeps <PATH>`

Caminho para adicionais *deps.json* arquivo.

`--additionalprobingpath <PATH>`

Caminho que contém a política de investigação e os assemblies a serem investigados.

`-d|--diagnostics`

Habilita a saída de diagnóstico.

`--fx-version <VERSION>`

A versão do tempo de execução do .NET Core instalado a ser usada para executar o aplicativo.

`-h|--help`

Imprime uma ajuda breve para o comando. Se estiver com `dotnet`, também imprimirá uma lista de comandos disponíveis.

`--info`

Imprime informações detalhadas sobre as ferramentas e o ambiente da CLI, como o sistema operacional atual, SHA de confirmação para a versão e outras informações.

`--roll-forward-on-no-candidate-fx`

 Efetua roll forward em nenhuma estrutura compartilhada candidata.

`-v|--verbose`

Habilita a saída detalhada.

`--version`

Imprime a versão do SDK do .NET Core em uso.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--additionalprobingpath <PATH>`

Caminho que contém a política de investigação e os assemblies a serem investigados.

`-d|--diagnostics`

Habilita a saída de diagnóstico.

`--fx-version <VERSION>`

A versão do tempo de execução do .NET Core instalado a ser usada para executar o aplicativo.

`-h|--help`

Imprime uma ajuda breve para o comando. Se estiver com `dotnet`, também imprimirá uma lista de comandos disponíveis.

`--info`

Imprime informações detalhadas sobre as ferramentas e o ambiente da CLI, como o sistema operacional atual, SHA de confirmação para a versão e outras informações.

`-v|--verbose`

Habilita a saída detalhada.

`--version`

Imprime a versão do SDK do .NET Core em uso.

---

## <a name="dotnet-commands"></a>Comandos dotnet

### <a name="general"></a>Geral

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

| Comando                             | Função                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)     | Compila um aplicativo .NET Core.                                     |
| [dotnet clean](dotnet-clean.md)     | Limpa saídas de build.                                              |
| [dotnet help](dotnet-help.md)       | Mostra uma documentação mais detalhada online para o comando.           |
| [dotnet migrate](dotnet-migrate.md) | Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.  |
| [dotnet msbuild](dotnet-msbuild.md) | Oferece acesso à linha de comando do MSBuild.                        |
| [dotnet new](dotnet-new.md)         | Inicializa um projeto do C# ou F# de um modelo especificado.                |
| [dotnet pack](dotnet-pack.md)       | Cria um pacote NuGet do seu código.                               |
| [dotnet publish](dotnet-publish.md) | Publica um aplicativo dependente do .NET Framework ou autocontido. |
| [dotnet restore](dotnet-restore.md) | Restaura as dependências para um determinado aplicativo.                  |
| [dotnet run](dotnet-run.md)         | Executa o aplicativo na origem.                                   |
| [dotnet sln](dotnet-sln.md)         | Opções para adicionar, remover e listar projetos em um arquivo de solução.       |
| [dotnet store](dotnet-store.md)     | Armazena os assemblies no repositório de pacotes de tempo de execução.                     |
| [dotnet test](dotnet-test.md)       | Executa testes usando um executor de teste.                                     |

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

| Comando                             | Função                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)     | Compila um aplicativo .NET Core.                                     |
| [dotnet clean](dotnet-clean.md)     | Limpa saídas de build.                                              |
| [dotnet migrate](dotnet-migrate.md) | Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.  |
| [dotnet msbuild](dotnet-msbuild.md) | Oferece acesso à linha de comando do MSBuild.                        |
| [dotnet new](dotnet-new.md)         | Inicializa um projeto do C# ou F# de um modelo especificado.                |
| [dotnet pack](dotnet-pack.md)       | Cria um pacote NuGet do seu código.                               |
| [dotnet publish](dotnet-publish.md) | Publica um aplicativo dependente do .NET Framework ou autocontido. |
| [dotnet restore](dotnet-restore.md) | Restaura as dependências para um determinado aplicativo.                  |
| [dotnet run](dotnet-run.md)         | Executa o aplicativo na origem.                                   |
| [dotnet sln](dotnet-sln.md)         | Opções para adicionar, remover e listar projetos em um arquivo de solução.       |
| [dotnet test](dotnet-test.md)       | Executa testes usando um executor de teste.                                     |

---

### <a name="project-references"></a>Referências de projeto

Comando | Função
--- | ---
[dotnet add reference](dotnet-add-reference.md) | Adicionar uma referência ao projeto.
[dotnet list reference](dotnet-list-reference.md) | Listar referências ao projeto.
[dotnet remove reference](dotnet-remove-reference.md) | Remover uma referência ao projeto.

### <a name="nuget-packages"></a>Pacotes NuGet

Comando | Função
--- | ---
[dotnet add package](dotnet-add-package.md) | Adicionar um pacote NuGet.
[dotnet remove package](dotnet-remove-package.md) | Remover um pacote NuGet.

### <a name="nuget-commands"></a>Comandos NuGet

Comando | Função
--- | ---
[dotnet nuget delete](dotnet-nuget-delete.md) | Exclui ou retira da lista um pacote do servidor.
[dotnet nuget locals](dotnet-nuget-locals.md) | Limpa ou lista os recursos locais do NuGet, como cache de solicitação http, cache temporário ou pasta de pacotes globais em todo o computador.
[dotnet nuget push](dotnet-nuget-push.md) | Envia um pacote ao servidor e os publica.

## <a name="examples"></a>Exemplos

Inicialize um aplicativo de console .NET Core de exemplo que pode ser compilado e executado:

`dotnet new console`

Restaure as dependências para um determinado aplicativo:

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Compile um projeto e suas dependências em um determinado diretório:

`dotnet build`

Execute um aplicativo dependente do framework chamado `myapp.dll`:

`dotnet myapp.dll`

## <a name="environment-variables"></a>Variáveis de ambiente

`DOTNET_PACKAGES`

O cache do pacote principal. Se não estiver definido, o padrão será `$HOME/.nuget/packages` em Unix ou `%HOME%\NuGet\Packages` no Windows.

`DOTNET_SERVICING`

Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o tempo de execução.

`DOTNET_CLI_TELEMETRY_OPTOUT`

Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft. Defina como `true` para cancelar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos); caso contrário, defina como `false` para cancelar os recursos de telemetria (os valores `false`, `0` ou `no`são aceitos). Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.
