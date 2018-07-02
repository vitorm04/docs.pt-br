---
title: Comando dotnet – CLI do .NET Core
description: Saiba mais sobre o comando dotnet (o driver genérico para as ferramentas da CLI do .NET Core) e seu uso.
author: mairaw
ms.author: mairaw
ms.date: 06/04/2018
ms.openlocfilehash: 788dc746705f9328683019ab3ad9836204a1ea63
ms.sourcegitcommit: fc70fcb9c789b6a4aefcdace46f3643fd076450f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34805653"
---
# <a name="dotnet-command"></a>Comando dotnet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nome

`dotnet` – Driver geral para executar os comandos da linha de comando.

## <a name="synopsis"></a>Sinopse

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```
---

## <a name="description"></a>Descrição

`dotnet` é um driver genérico para a cadeia de ferramentas da CLI (Interface de Linha de Comando). Invocado por conta própria, ele fornece breve instruções de uso.

Cada recurso específico é implementado como um comando. Para usar o recurso, o comando é especificado após `dotnet`, como [`dotnet build`](dotnet-build.md). Todos os argumentos após o comando são seus próprios argumentos.

A única vez que `dotnet` é usado como um comando em si é ao executar [aplicativos dependentes da estrutura](../deploying/index.md). Especifique uma DLL de aplicativo após o verbo `dotnet` para executar o aplicativo (por exemplo, `dotnet myapp.dll`).

## <a name="options"></a>Opções

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`--additional-deps <PATH>`

Caminho para o arquivo *deps.json* adicional.

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

`--list-runtimes`

Exibe os tempos de execução do .NET Core instalado.

`--list-sdks`

Exibe os tempos de execução dos SDKs .NET Core instalados.

`--roll-forward-on-no-candidate-fx`

 Efetua roll forward em nenhuma estrutura compartilhada candidata.

`-v|--verbosity <LEVEL>`

Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`. Não compatível com todos os comandos. Veja a página de comando específica para determinar se essa opção está disponível.

`--version`

Imprime a versão do SDK do .NET Core em uso.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`--additional-deps <PATH>`

Caminho para o arquivo *deps.json* adicional.

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

`-v|--verbosity <LEVEL>`

Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`. Não compatível com todos os comandos. Veja a página de comando específica para determinar se essa opção está disponível.

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

`-v|--verbosity <LEVEL>`

Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`. Não compatível com todos os comandos. Veja a página de comando específica para determinar se essa opção está disponível.

`--version`

Imprime a versão do SDK do .NET Core em uso.

---

## <a name="dotnet-commands"></a>Comandos dotnet

### <a name="general"></a>Geral

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

| Comando                                       | Função                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)               | Compila um aplicativo .NET Core.                                     |
| [dotnet build-server](dotnet-build-server.md) | Interage com servidores iniciados por um build.                          |
| [dotnet clean](dotnet-clean.md)               | Limpa saídas de build.                                                |
| [dotnet help](dotnet-help.md)                 | Mostra uma documentação mais detalhada online para o comando.           |
| [dotnet migrate](dotnet-migrate.md)           | Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.  |
| [dotnet msbuild](dotnet-msbuild.md)           | Oferece acesso à linha de comando do MSBuild.                        |
| [dotnet new](dotnet-new.md)                   | Inicializa um projeto do C# ou F# de um modelo especificado.                |
| [dotnet pack](dotnet-pack.md)                 | Cria um pacote NuGet do seu código.                               |
| [dotnet publish](dotnet-publish.md)           | Publica um aplicativo dependente do .NET Framework ou autocontido. |
| [dotnet restore](dotnet-restore.md)           | Restaura as dependências para um determinado aplicativo.                  |
| [dotnet run](dotnet-run.md)                   | Executa o aplicativo na origem.                                   |
| [dotnet sln](dotnet-sln.md)                   | Opções para adicionar, remover e listar projetos em um arquivo de solução.       |
| [dotnet store](dotnet-store.md)               | Armazena os assemblies no repositório de pacotes de tempo de execução.                     |
| [dotnet test](dotnet-test.md)                 | Executa testes usando um executor de teste.                                     |

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

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
[dotnet add reference](dotnet-add-reference.md) | Adiciona uma referência ao projeto.
[dotnet list reference](dotnet-list-reference.md) | Lista referências ao projeto.
[dotnet remove reference](dotnet-remove-reference.md) | Remove uma referência ao projeto.

### <a name="nuget-packages"></a>Pacotes NuGet

Comando | Função
--- | ---
[dotnet add package](dotnet-add-package.md) | Adiciona um pacote NuGet.
[dotnet remove package](dotnet-remove-package.md) | Remove um pacote NuGet.

### <a name="nuget-commands"></a>Comandos NuGet

Comando | Função
--- | ---
[dotnet nuget delete](dotnet-nuget-delete.md) | Exclui ou retira da lista um pacote do servidor.
[dotnet nuget locals](dotnet-nuget-locals.md) | Limpa ou lista os recursos locais do NuGet, como cache de solicitação http, cache temporário ou pasta de pacotes globais em todo o computador.
[dotnet nuget push](dotnet-nuget-push.md) | Envia um pacote ao servidor e os publica.

### <a name="global-tools-commands"></a>Comandos de ferramentas globais

[Ferramentas Globais do .NET Core](global-tools.md) estão disponíveis a partir do SDK do .NET Core 2.1.300:

Comando | Função
--- | ---
[dotnet tool install](dotnet-tool-install.md) | Instala uma Ferramenta Global no seu computador.
[dotnet tool list](dotnet-tool-list.md) | Lista todas as Ferramentas Globais atualmente instaladas no diretório padrão do computador ou no caminho especificado.
[dotnet tool uninstall](dotnet-tool-uninstall.md) | Desinstala uma Ferramenta Global do computador.
[dotnet tool update](dotnet-tool-update.md) | Atualiza uma Ferramenta Global no computador.

### <a name="additional-tools"></a>Ferramentas adicionais

A partir do SDK do .NET Core 2.1.300, várias ferramentas que estavam disponíveis apenas por projeto usando `DotnetCliToolReference` agora estão disponíveis como parte do SDK do .NET Core. Essas ferramentas incluem:

| Ferramenta                                              | Função                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| dev-certs                                         | Cria e gerencia certificados de desenvolvimento.                |
| [ef](/ef/core/miscellaneous/cli/dotnet)           | Ferramentas de linha de comando do Entity Framework Core.                    |
| sql-cache                                         | Ferramentas de linha de comando de cache do SQL Server.                         |
| [user-secrets](/aspnet/core/security/app-secrets) | Gerencia os segredos do usuário de desenvolvimento.                            |
| [watch](/aspnet/core/tutorials/dotnet-watch)      | Inicia um observador de arquivo que executa um comando quando os arquivos são alterados. |

Para saber mais sobre cada ferramenta, execute `dotnet <tool-name> --help`.

## <a name="examples"></a>Exemplos

Cria um novo aplicativo de console do .NET Core:

`dotnet new console`

Restaure as dependências para um determinado aplicativo:

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Compile um projeto e suas dependências em um determinado diretório:

`dotnet build`

Execute um aplicativo dependente do framework chamado `myapp.dll`:

`dotnet myapp.dll`

## <a name="environment-variables"></a>Variáveis de ambiente

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`DOTNET_PACKAGES`

O cache do pacote principal. Se não estiver definido, o padrão será `$HOME/.nuget/packages` em Unix ou `%HOME%\NuGet\Packages` no Windows.

`DOTNET_SERVICING`

Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o tempo de execução.

`DOTNET_CLI_TELEMETRY_OPTOUT`

Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft. Definido como `true` para recusar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos). Caso contrário, definido como `false` para aceitar os recursos de telemetria (os valores `false`, `0` ou `no` são aceitos). Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.

`DOTNET_MULTILEVEL_LOOKUP`

Especifica se o tempo de execução, a estrutura compartilhada ou o SDK do .NET Core são resolvidos no local global. Se não estiver definida, o padrão será `true`. Definida como `false` para não resolver no local global e ter instalações do NET Core isoladas (os valores `0` ou `false` são aceitos). Para obter mais informações sobre a pesquisa de vários níveis, consulte [Pesquisa SharedFX de vários níveis](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

Desativa o roll forward da versão secundária. Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`DOTNET_PACKAGES`

O cache do pacote principal. Se não estiver definido, o padrão será `$HOME/.nuget/packages` em Unix ou `%HOME%\NuGet\Packages` no Windows.

`DOTNET_SERVICING`

Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o tempo de execução.

`DOTNET_CLI_TELEMETRY_OPTOUT`

Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft. Definido como `true` para recusar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos). Caso contrário, definido como `false` para aceitar os recursos de telemetria (os valores `false`, `0` ou `no` são aceitos). Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.

`DOTNET_MULTILEVEL_LOOKUP`

Especifica se o tempo de execução, a estrutura compartilhada ou o SDK do .NET Core são resolvidos no local global. Se não estiver definida, o padrão será `true`. Definida como `false` para não resolver no local global e ter instalações do NET Core isoladas (os valores `0` ou `false` são aceitos). Para obter mais informações sobre a pesquisa de vários níveis, consulte [Pesquisa SharedFX de vários níveis](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`DOTNET_PACKAGES`

O cache do pacote principal. Se não estiver definido, o padrão será `$HOME/.nuget/packages` em Unix ou `%HOME%\NuGet\Packages` no Windows.

`DOTNET_SERVICING`

Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o tempo de execução.

`DOTNET_CLI_TELEMETRY_OPTOUT`

Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft. Definido como `true` para recusar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos). Caso contrário, definido como `false` para aceitar os recursos de telemetria (os valores `false`, `0` ou `no` são aceitos). Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.

---
