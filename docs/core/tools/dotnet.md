---
title: Comando dotnet
description: Saiba mais sobre o comando dotNet (o Driver genérico para o CLI do .NET Core) e seu uso.
ms.date: 02/13/2020
ms.openlocfilehash: da37c5cc3b019851e245fa3f65ae9dfb8a3fef54
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240864"
---
# <a name="dotnet-command"></a>Comando dotnet

**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores

## <a name="name"></a>Nome

`dotnet`-o Driver genérico para o CLI do .NET Core.

## <a name="synopsis"></a>Sinopse

Para obter informações sobre os comandos disponíveis e o ambiente:

```dotnetcli
dotnet [-h|--help] [--version] [--info]
    [--list-runtimes] [--list-sdks]
```

Para executar um comando (requer a instalação do SDK):

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity]
    [command-options] [arguments]
```

Para executar um aplicativo:

```dotnetcli
dotnet [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]
```

`--roll-forward` está disponível desde o .NET Core 3. x. Use `--roll-forward-on-no-candidate-fx` para .NET Core 2. x.

## <a name="description"></a>DESCRIÇÃO

O comando `dotnet` tem duas funções:

- Ele fornece comandos para trabalhar com projetos do .NET Core.

  Por exemplo, [`dotnet build`](dotnet-build.md) compila um projeto. Cada comando define suas próprias opções e argumentos. Todos os comandos dão suporte à opção `--help` para imprimir uma breve documentação sobre como usar o comando.

- Ele executa aplicativos .NET Core.

  Especifique o caminho para um arquivo de `.dll` de aplicativo para executar o aplicativo. Por exemplo, `dotnet myapp.dll` executa o aplicativo `myapp`. Consulte [implantação de aplicativos do .NET Core](../deploying/index.md) para saber mais sobre as opções de implantação.

## <a name="options"></a>Opções

Opções diferentes estão disponíveis para `dotnet` por si só, para executar um comando e para executar um aplicativo.

### <a name="options-for-dotnet-by-itself"></a>Opções para dotnet por si só

As opções a seguir são para `dotnet` por si só. Por exemplo, `dotnet --info`. Eles imprimem informações sobre o ambiente.

- **`--info`**

  Imprime informações detalhadas sobre uma instalação do .NET Core e o ambiente do computador, como o sistema operacional atual, e o SHA da confirmação da versão do .NET Core.

- **`--version`**

  Imprime a versão do SDK do .NET Core em uso.

- **`--list-runtimes`**

  Imprime uma lista de tempos de execução do .NET Core instalados.

- **`--list-sdks`**

  Imprime uma lista de SDKs do .NET Core instalados.

- **`-h|--help`**

  Imprime uma lista de comandos disponíveis.

### <a name="sdk-options-for-running-a-command"></a>Opções do SDK para executar um comando

As opções a seguir são para `dotnet` com um comando. Por exemplo, `dotnet build --help`.

- **`-d|--diagnostics`**

  Habilita a saída de diagnóstico.

- **`-v|--verbosity <LEVEL>`**

  Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`. Sem suporte em todos os comandos. Consulte a página de comando específica para determinar se essa opção está disponível.

- **`-h|--help`**

  Imprime a documentação para um determinado comando, como `dotnet build --help`.

- **`command options`**

  Cada comando define opções específicas para esse comando. Consulte a página de comando específica para obter uma lista de opções disponíveis.

### <a name="runtime-options"></a>Opções de tempo de execução

As opções a seguir estão disponíveis quando `dotnet` executa um aplicativo. Por exemplo, `dotnet myapp.dll --fx-version 3.1.1`.

- **`--additionalprobingpath <PATH>`**

  Caminho que contém a política de investigação e os assemblies a serem investigados.

- **`--additional-deps <PATH>`**

  Caminho para um arquivo *.deps.json* adicional. Um arquivo *deps. JSON* contém uma lista de dependências, dependências de compilação e informações de versão usadas para resolver conflitos de assembly. Para obter mais informações, confira [Arquivos de configuração de runtime](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) no GitHub.

- **`--fx-version <VERSION>`**

  Versão do runtime do .NET Core a ser usada para executar o aplicativo.

- **`--runtimeconfig`**

  Caminho para um arquivo *runtimeconfig.json*. Um arquivo *runtimeconfig. JSON* é um arquivo de configuração que contém configurações de tempo de execução. Para obter mais informações, consulte [definições de configuração de tempo de execução do .NET Core](../run-time-config/index.md#runtimeconfigjson).

- **`--roll-forward-on-no-candidate-fx <N>`** **disponível no SDK do .NET Core 2. x.**

  Define o comportamento quando a estrutura compartilhada necessária não está disponível. `N` pode ser:

  - `0` – Desabilitar até mesmo o roll forward da versão secundária.
  - `1` – Efetuar roll forward da versão secundária, mas não da versão principal. Esse é o comportamento padrão.
  - `2` – Efetuar roll forward das versões secundária e principal.

   Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).

- **`--roll-forward <SETTING>`** **disponível a partir do SDK do .NET Core 3,0.**

  Controla como o roll forward é aplicado ao aplicativo. O `SETTING` pode ser um dos valores a seguir. Se não for especificado, `Minor` será o padrão.

  - `LatestPatch`-roll forward para a versão mais alta do patch. Isso desabilita o roll forward da versão secundária.
  - `Minor`-roll forward para a versão secundária mais baixa, se a versão secundária solicitada estiver ausente. Se a versão secundária solicitada estiver presente, a política LatestPatch será usada.
  - `Major`-rolar para a versão principal mais baixa e a versão secundária mais baixa, se a versão principal solicitada estiver ausente. Se a versão principal solicitada estiver presente, a política secundária será usada.
  - `LatestMinor`-roll forward até a versão secundária mais alta, mesmo que a versão secundária solicitada esteja presente. Destinado a cenários de hospedagem de componente.
  - `LatestMajor`-roll forward até a versão secundária mais alta e a mais alta, mesmo que a principal solicitada esteja presente. Destinado a cenários de hospedagem de componente.
  - `Disable`-não rolar para frente. Associar somente à versão especificada. Essa política não é recomendada para uso geral, pois ela desabilita a capacidade de efetuar roll forward para os patches mais recentes. Esse valor só é recomendado para teste.

Com exceção de `Disable`, todas as configurações usarão a versão de patch mais alta disponível.

O comportamento de roll forward também pode ser configurado em uma propriedade de arquivo de projeto, uma propriedade de arquivo de configuração de tempo de execução e uma variável de ambiente. Para obter mais informações, consulte [roll forward de tempo de execução de versão principal](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).

## <a name="dotnet-commands"></a>Comandos dotnet

### <a name="general"></a>Geral

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
| [dotnet store](dotnet-store.md)               | Armazena os assemblies no repositório de pacotes de runtime.                     |
| [dotnet test](dotnet-test.md)                 | Executa testes usando um executor de teste.                                     |

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

### <a name="global-tool-path-and-local-tools-commands"></a>Comandos globais, de caminho de ferramenta e de ferramentas locais

Ferramentas são aplicativos de console que são instalados a partir de pacotes NuGet e são invocados no prompt de comando. Você pode escrever ferramentas por conta própria ou instalar ferramentas escritas por terceiros. As ferramentas também são conhecidas como ferramentas globais, ferramentas de caminho de ferramenta e ferramentas locais. Para obter mais informações, consulte [visão geral das ferramentas do .NET Core](global-tools.md). As ferramentas globais e de caminho de ferramenta estão disponíveis a partir do SDK do .NET Core 2,1. As ferramentas locais estão disponíveis a partir do SDK do .NET Core 3,0.

Comando | Função
--- | ---
[dotnet tool install](dotnet-tool-install.md) | Instala uma ferramenta em seu computador.
[dotnet tool list](dotnet-tool-list.md) | Lista todas as ferramentas globais, ferramentas-caminho ou locais atualmente instaladas no seu computador.
[dotnet tool uninstall](dotnet-tool-uninstall.md) | Desinstala uma ferramenta do seu computador.
[dotnet tool update](dotnet-tool-update.md) | Atualiza uma ferramenta instalada em seu computador.

### <a name="additional-tools"></a>Ferramentas adicionais

A partir do SDK do .NET Core 2.1.300, várias ferramentas que estavam disponíveis apenas por projeto usando `DotnetCliToolReference` agora estão disponíveis como parte do SDK do .NET Core. Essas ferramentas estão listadas na tabela a seguir:

| Ferramenta                                              | Função                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| dev-certs                                         | Cria e gerencia certificados de desenvolvimento.                |
| [ef](/ef/core/miscellaneous/cli/dotnet)           | Ferramentas de linha de comando do Entity Framework Core.                    |
| sql-cache                                         | Ferramentas de linha de comando de cache do SQL Server.                         |
| [user-secrets](/aspnet/core/security/app-secrets) | Gerencia os segredos do usuário de desenvolvimento.                            |
| [watch](/aspnet/core/tutorials/dotnet-watch)      | Inicia um observador de arquivo que executa um comando quando os arquivos são alterados. |

Para obter mais informações sobre cada ferramenta, digite `dotnet <tool-name> --help`.

## <a name="examples"></a>Exemplos

Crie um novo aplicativo de console .NET Core:

```dotnetcli
dotnet new console
```

Compile um projeto e suas dependências em um determinado diretório:

```dotnetcli
dotnet build
```

Executar um aplicativo:

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a>Variáveis de ambiente

- `DOTNET_ROOT`, `DOTNET_ROOT(x86)`

  Especifica o local dos tempos de execução do .NET Core, se eles não estiverem instalados no local padrão. O local padrão no Windows é `C:\Program Files\dotnet`. O local padrão no Linux e no macOS é `/usr/share/dotnet`. Essa variável de ambiente é usada somente ao executar aplicativos por meio de executáveis gerados (apphosts). `DOTNET_ROOT(x86)` é usado em vez de executar um executável de 32 bits em um sistema operacional de 64 bits.

- `DOTNET_PACKAGES`

  A pasta de pacotes globais. Se não estiver definido, o padrão será `~/.nuget/packages` em Unix ou `%userprofile%\.nuget\packages` no Windows.

- `DOTNET_SERVICING`

  Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o runtime.

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft. Definido como `true` para recusar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos). Caso contrário, definido como `false` para aceitar os recursos de telemetria (os valores `false`, `0` ou `no` são aceitos). Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.

- `DOTNET_MULTILEVEL_LOOKUP`

  Especifica se o runtime, a estrutura compartilhada ou o SDK do .NET Core são resolvidos no local global. Se não estiver definido, o padrão será 1 (`true`lógico). Defina como 0 (`false`lógico) para não resolver a partir do local global e ter instalações isoladas do .NET Core. Para obter mais informações sobre a pesquisa de vários níveis, consulte [Pesquisa SharedFX de vários níveis](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

- `DOTNET_ROLL_FORWARD` **disponível a partir do SDK do .NET Core 3. x.**

  Determina o comportamento de roll-forward. Para obter mais informações, consulte a opção `--roll-forward` anteriormente neste artigo.

- `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **disponível no SDK do .NET Core 2. x.**

  Desabilita o roll forward da versão secundária, se definido como `0`. Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).

- `DOTNET_CLI_UI_LANGUAGE`

  Define o idioma da interface do usuário da CLI usando um valor de localidade, como `en-us`. Os valores com suporte são os mesmos para o Visual Studio. Para obter mais informações, consulte a seção sobre como alterar o idioma do instalador na [documentação de instalação do Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019). As regras do Gerenciador de recursos do .NET se aplicam, portanto, você não precisa escolher uma correspondência exata&mdash;também pode escolher os descendentes na árvore de `CultureInfo`. Por exemplo, se você defini-lo como `fr-CA`, a CLI encontrará e usará as traduções `fr`. Se você defini-lo como um idioma sem suporte, a CLI voltará para o inglês.

- `DOTNET_DISABLE_GUI_ERRORS`

  Para executáveis gerados por GUI habilitado-desabilita o Popup da caixa de diálogo que normalmente mostra para determinadas classes de erros. Ele só grava em `stderr` e sai nesses casos.
  
- `DOTNET_ADDITIONAL_DEPS`

  Equivalente à opção da CLI `--additional-deps`.

- `DOTNET_RUNTIME_ID`

  Substitui o RID detectado.

- `DOTNET_SHARED_STORE`

  Local do "armazenamento compartilhado" para o qual a resolução de assembly volta para em alguns casos.

- `DOTNET_STARTUP_HOOKS`

  Lista de assemblies dos quais carregar e executar os ganchos de inicialização.

- `COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`

  Controla o rastreamento de diagnóstico dos componentes de hospedagem, como `dotnet.exe`, `hostfxr`e `hostpolicy`.

## <a name="see-also"></a>Confira também

- [Arquivos de configuração de runtime](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [Definições de configuração de tempo de execução do .NET Core](../run-time-config/index.md)
