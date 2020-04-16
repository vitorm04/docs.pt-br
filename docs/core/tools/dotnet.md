---
title: Comando dotnet
description: Saiba mais sobre o comando dotnet (o driver genérico para o .NET Core CLI) e seu uso.
ms.date: 02/13/2020
ms.openlocfilehash: d700f35f3c977524ff3857da99519882eb0136e9
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463269"
---
# <a name="dotnet-command"></a>Comando dotnet

**Este artigo se aplica a:** ✔️ .NET Core 2.1 SDK e versões posteriores

## <a name="name"></a>Nome

`dotnet`- O driver genérico para o .NET Core CLI.

## <a name="synopsis"></a>Sinopse

Para obter informações sobre os comandos disponíveis e o ambiente:

```dotnetcli
dotnet [--version] [--info] [--list-runtimes] [--list-sdks]

dotnet -h|--help
```

Para executar um comando (requer instalação do SDK):

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity <LEVEL>]
    [command-options] [arguments]
```

Para executar um aplicativo:

```dotnetcli
dotnet [--additionalprobingpath <PATH>] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]
```

`--roll-forward`está disponível desde .NET Core 3.x. Use `--roll-forward-on-no-candidate-fx` para .NET Core 2.x.

## <a name="description"></a>Descrição

O `dotnet` comando tem duas funções:

- Ele fornece comandos para trabalhar com projetos .NET Core.

  Por exemplo, [`dotnet build`](dotnet-build.md) constrói um projeto. Cada comando define suas próprias opções e argumentos. Todos os comandos suportam a `--help` opção de imprimir breve documentação sobre como usar o comando.

- Ele executa aplicativos .NET Core.

  Você especifica o caminho `.dll` para um arquivo de aplicativo para executar o aplicativo.  Para executar o aplicativo significa encontrar e executar o ponto de `Main` entrada, que no caso de aplicativos de console é o método. Por exemplo, `dotnet myapp.dll` `myapp` executa o aplicativo. Consulte a [implantação do aplicativo .NET Core](../deploying/index.md) para saber sobre opções de implantação.

## <a name="options"></a>Opções

Diferentes opções `dotnet` estão disponíveis para si só, para executar um comando e para executar um aplicativo.

### <a name="options-for-dotnet-by-itself"></a>Opções para dotnet por si só

As seguintes `dotnet` opções são para si só. Por exemplo, `dotnet --info`. Eles imprimem informações sobre o meio ambiente.

- **`--info`**

  Imprime informações detalhadas sobre uma instalação do .NET Core e o ambiente do computador, como o sistema operacional atual, e o SHA da confirmação da versão do .NET Core.

- **`--version`**

  Imprime a versão do SDK do .NET Core em uso.

- **`--list-runtimes`**

  Imprime uma lista dos tempos de execução do .NET Core instalados. Uma versão x86 do SDK lista apenas tempos de execução x86, e uma versão x64 do SDK lista apenas tempos de execução x64.

- **`--list-sdks`**

  Imprime uma lista dos SDKs do Núcleo .NET instalados.

- **`-h|--help`**

  Imprime uma lista de comandos disponíveis.

### <a name="sdk-options-for-running-a-command"></a>Opções de SDK para executar um comando

As seguintes `dotnet` opções são para com um comando. Por exemplo, `dotnet build --help`.

- **`-d|--diagnostics`**

  Habilita a saída de diagnóstico.

- **`-v|--verbosity <LEVEL>`**

  Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`. Não suportado em todos os comandos. Consulte a página de comando específica para determinar se essa opção está disponível.

- **`-h|--help`**

  Imprime a documentação para um determinado comando, como `dotnet build --help`.

- **`command options`**

  Cada comando define opções específicas para esse comando. Consulte a página de comando específica para obter uma lista de opções disponíveis.

### <a name="runtime-options"></a>Opções de tempo de execução

As seguintes opções estão disponíveis quando `dotnet` executa um aplicativo. Por exemplo, `dotnet myapp.dll --fx-version 3.1.1`.

- **`--additionalprobingpath <PATH>`**

  Caminho que contém a política de investigação e os assemblies a serem investigados.

- **`--additional-deps <PATH>`**

  Caminho para um arquivo *.deps.json* adicional. Um arquivo *deps.json* contém uma lista de dependências, dependências de compilação e informações de versão usadas para lidar com conflitos de montagem. Para obter mais informações, confira [Arquivos de configuração de runtime](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) no GitHub.

- **`--fx-version <VERSION>`**

  Versão do runtime do .NET Core a ser usada para executar o aplicativo.

- **`--runtimeconfig`**

  Caminho para um arquivo *runtimeconfig.json*. Um arquivo *runtimeconfig.json* é um arquivo de configuração que contém configurações em tempo de execução. Para obter mais informações, consulte [as configurações de configuração em tempo de execução do .NET Core](../run-time-config/index.md#runtimeconfigjson).

- **`--roll-forward-on-no-candidate-fx <N>`****Disponível em .NET Core 2.x SDK.**

  Define o comportamento quando a estrutura compartilhada necessária não está disponível. `N` pode ser:

  - `0` – Desabilitar até mesmo o roll forward da versão secundária.
  - `1` – Efetuar roll forward da versão secundária, mas não da versão principal. Esse é o comportamento padrão.
  - `2` – Efetuar roll forward das versões secundária e principal.

   Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).

- **`--roll-forward <SETTING>`****Disponível a partir de .NET Core SDK 3.0.**

  Controla como o roll forward é aplicado ao aplicativo. O `SETTING` pode ser um dos seguintes valores. Se não for `Minor` especificado, é o padrão.

  - `LatestPatch`- Avance para a versão mais alta do patch. Isso desabilita o roll forward da versão secundária.
  - `Minor`- Encaminhe para a versão menor mais baixa, se a versão menor solicitada estiver faltando. Se a versão secundária solicitada estiver presente, a política LatestPatch será usada.
  - `Major`- Avance para a versão principal mais baixa e a versão menor mais baixa, se a versão principal solicitada estiver faltando. Se a versão principal solicitada está presente, a política Secundária é usada.
  - `LatestMinor`- Encaminhe para a versão menor mais alta, mesmo que a versão menor solicitada esteja presente. Destinado a cenários de hospedagem de componente.
  - `LatestMajor`- Avance para a versão mais alta e menor, mesmo que o major solicitado esteja presente. Destinado a cenários de hospedagem de componente.
  - `Disable`- Não role para a frente. Associar somente à versão especificada. Essa política não é recomendada para uso geral, pois ela desabilita a capacidade de efetuar roll forward para os patches mais recentes. Esse valor só é recomendado para teste.

Com exceção `Disable`de , todas as configurações usarão a versão de patch mais alta disponível.

O comportamento de encaminhamento também pode ser configurado em uma propriedade de arquivo de projeto, uma propriedade de arquivo de configuração em tempo de execução e uma variável de ambiente. Para obter mais informações, consulte [o tempo de execução da versão principal para a frente](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).

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
[dotnet nuget push](dotnet-nuget-push.md) | Envia um pacote ao servidor e os publica.
[dotnet nuget locals](dotnet-nuget-locals.md) | Limpa ou lista os recursos locais do NuGet, como cache de solicitação http, cache temporário ou pasta de pacotes globais em todo o computador.
[dotnet nuget add source](dotnet-nuget-add-source.md) | Adiciona uma fonte NuGet.
[dotnet nuget disable source](dotnet-nuget-disable-source.md) | Desativa uma fonte NuGet.
[dotnet nuget enable source](dotnet-nuget-enable-source.md) | Habilita uma fonte NuGet.
[dotnet nuget list source](dotnet-nuget-list-source.md) | Lista todas as fontes NuGet configuradas.
[dotnet nuget remove source](dotnet-nuget-remove-source.md) | Remove uma fonte NuGet.
[dotnet nuget update source](dotnet-nuget-update-source.md) | Atualiza uma fonte NuGet.

### <a name="global-tool-path-and-local-tools-commands"></a>Comandos de ferramentas globais, de caminho de ferramentas e locais

As ferramentas são aplicativos de console que são instalados a partir de pacotes NuGet e são invocados a partir do prompt de comando. Você mesmo pode escrever ferramentas ou instalar ferramentas escritas por terceiros. As ferramentas também são conhecidas como ferramentas globais, ferramentas de caminho de ferramentas e ferramentas locais. Para obter mais informações, consulte [a visão geral das ferramentas .NET Core](global-tools.md). Ferramentas globais e de caminho de ferramentas estão disponíveis a partir do .NET Core SDK 2.1. As ferramentas locais estão disponíveis a partir do .NET Core SDK 3.0.

Comando | Função
--- | ---
[dotnet tool install](dotnet-tool-install.md) | Instala uma ferramenta em sua máquina.
[dotnet tool list](dotnet-tool-list.md) | Lista todas as ferramentas globais, de caminho de ferramentas ou locais atualmente instaladas em sua máquina.
[dotnet tool uninstall](dotnet-tool-uninstall.md) | Desinstala uma ferramenta da sua máquina.
[dotnet tool update](dotnet-tool-update.md) | Atualiza uma ferramenta instalada em sua máquina.

### <a name="additional-tools"></a>Ferramentas adicionais

A partir do SDK do .NET Core 2.1.300, várias ferramentas que estavam disponíveis apenas por projeto usando `DotnetCliToolReference` agora estão disponíveis como parte do SDK do .NET Core. Essas ferramentas estão listadas na tabela a seguir:

| Ferramenta                                              | Função                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| dev-certs                                         | Cria e gerencia certificados de desenvolvimento.                |
| [Ef](/ef/core/miscellaneous/cli/dotnet)           | Ferramentas de linha de comando do Entity Framework Core.                    |
| sql-cache                                         | Ferramentas de linha de comando de cache do SQL Server.                         |
| [user-secrets](/aspnet/core/security/app-secrets) | Gerencia os segredos do usuário de desenvolvimento.                            |
| [Assistir](/aspnet/core/tutorials/dotnet-watch)      | Inicia um observador de arquivo que executa um comando quando os arquivos são alterados. |

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

Execute um aplicativo:

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a>Variáveis de ambiente

- `DOTNET_ROOT`, `DOTNET_ROOT(x86)`

  Especifica a localização dos tempos de execução do .NET Core, se eles não estiverem instalados no local padrão. O local padrão `C:\Program Files\dotnet`no Windows é . A localização padrão no Linux `/usr/share/dotnet`e macOS é . Essa variável de ambiente é usada apenas ao executar aplicativos através de executáveis gerados (apphosts). `DOTNET_ROOT(x86)`é usado em vez disso ao executar um executável de 32 bits em um sistema operacional de 64 bits.

- `DOTNET_PACKAGES`

  A pasta de pacotes globais. Se não estiver definido, o padrão será `~/.nuget/packages` em Unix ou `%userprofile%\.nuget\packages` no Windows.

- `DOTNET_SERVICING`

  Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o runtime.

- `DOTNET_NOLOGO`

  Especifica se as mensagens de boas-vindas e telemetria do .NET Core são exibidas na primeira execução. Definir `true` para silenciar essas mensagens `true` `1` `yes` (valores , ou `false` aceitos) `false` `0`ou `no` definido para permitir (valores , ou aceitos). Se não estiver definido, o padrão é `false` e as mensagens serão exibidas na primeira execução. Observe que esta bandeira não tem efeito `DOTNET_CLI_TELEMETRY_OPTOUT` na telemetria (veja para optar por não enviar telemetria).

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft. Definido como `true` para recusar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos). Caso contrário, definido como `false` para aceitar os recursos de telemetria (os valores `false`, `0` ou `no` são aceitos). Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.

- `DOTNET_MULTILEVEL_LOOKUP`

  Especifica se o runtime, a estrutura compartilhada ou o SDK do .NET Core são resolvidos no local global. Se não for definido, ele `true`é padrão para 1 (lógico ). Definir como 0 `false`(lógico ) para não resolver a partir do local global e ter instalações isoladas .NET Core. Para obter mais informações sobre a pesquisa de vários níveis, consulte [Pesquisa SharedFX de vários níveis](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

- `DOTNET_ROLL_FORWARD`**Disponível a partir de .NET Core 3.x SDK.**

  Determina o comportamento de rolagem para a frente. Para obter mais `--roll-forward` informações, consulte a opção no início deste artigo.

- `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`**Disponível em .NET Core 2.x SDK.**

  Desabilita o roll forward da versão secundária, se definido como `0`. Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).

- `DOTNET_CLI_UI_LANGUAGE`

  Define a linguagem da IU CLI usando `en-us`um valor local, como . Os valores suportados são os mesmos do Visual Studio. Para obter mais informações, consulte a seção sobre a alteração do idioma do instalador na [documentação](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019)de instalação do Visual Studio . As regras do gerenciador de recursos .NET se aplicam,&mdash;para que você não `CultureInfo` tenha que escolher uma correspondência exata, você também pode escolher descendentes na árvore. Por exemplo, se você `fr-CA`defini-lo para , `fr` o CLI encontrará e usará as traduções. Se você defini-lo para um idioma que não é suportado, o CLI volta para o inglês.

- `DOTNET_DISABLE_GUI_ERRORS`

  Para executáveis gerados habilitados por GUI - desativa o popup de diálogo, que normalmente é mostrada para determinadas classes de erros. Ele só `stderr` escreve e sai nesses casos.
  
- `DOTNET_ADDITIONAL_DEPS`

  Equivalente à `--additional-deps`opção CLI .

- `DOTNET_RUNTIME_ID`

  Substitui o RID detectado.

- `DOTNET_SHARED_STORE`

  A localização da "loja compartilhada" que a resolução do conjunto recua em alguns casos.

- `DOTNET_STARTUP_HOOKS`

  Lista de montagens para carregar e executar ganchos de inicialização.

- `COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`

  Controla o rastreamento de diagnósticos dos `dotnet.exe`componentes de hospedagem, tais como , `hostfxr`e `hostpolicy`.

## <a name="see-also"></a>Confira também

- [Arquivos de configuração de runtime](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [Configurações de configuração de tempo de execução do .NET Core](../run-time-config/index.md)
