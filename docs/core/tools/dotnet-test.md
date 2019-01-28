---
title: Comando dotnet test
description: O comando dotnet test é usado para executar testes de unidade em um determinado projeto.
ms.date: 05/29/2018
ms.openlocfilehash: 1b2a3917a930db0c0a49ebea41f568aaf4a58ee3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54535276"
---
# <a name="dotnet-test"></a>dotnet test

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nome

`dotnet test` - driver de teste do .NET usado para executar testes de unidade.

## <a name="synopsis"></a>Sinopse

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] 
    [-v|--verbosity] [-- <RunSettings arguments>]

dotnet test [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]

dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```console
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]

dotnet test [-h|--help]
```

---

## <a name="description"></a>Descrição

O comando `dotnet test` é usado para executar testes de unidade em um determinado projeto. O comando `dotnet test` inicia o aplicativo de console executor de teste especificado para um projeto. O executor de teste realiza os testes definidos para uma estrutura de teste de unidade (por exemplo, MSTest, NUnit ou xUnit) e relata o êxito ou a falha de cada teste. Se todos os testes forem bem-sucedidos, o executor de testes retornará 0 como um código de saída; caso contrário, se algum teste falhar, retornará 1. O executor de teste e a biblioteca de teste de unidade são empacotados como pacotes NuGet e são restaurados como dependências comuns para o projeto.

Os projetos de teste especificam o executor de teste usando um elemento comum `<PackageReference>`, conforme mostrado no exemplo de arquivo de projeto a seguir:

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a>Arguments

`PROJECT`

Caminho para o projeto de teste. Se não é especificado, usa como padrão o diretório atual.

## <a name="options"></a>Opções

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

Usa os adaptadores de teste personalizado do caminho especificado na execução de teste.

`--blame`

Executa os testes no modo blame. Essa opção é útil para isolar os testes problemáticos que causam uma falha do host de teste. Ela cria um arquivo de saída no diretório atual como *Sequence.xml* que captura a ordem de execução dos testes antes da falha.

`-c|--configuration {Debug|Release}`

Define a configuração da compilação. O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

Habilita o coletor de dados para a execução de teste. Para obter mais informações, consulte [Monitor and analyze test run](https://aka.ms/vstest-collect) (Monitorar e analisar a execução de teste).

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico para o arquivo especificado.

`-f|--framework <FRAMEWORK>`

Procura os binários de teste para uma [estrutura](../../standard/frameworks.md) específica.

`--filter <EXPRESSION>`

Filtra os testes no projeto atual usando a expressão especificada. Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details). Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).

`-h|--help`

Imprime uma ajuda breve para o comando.

`-l|--logger <LoggerUri/FriendlyName>`

Especifica um agente para resultados do teste.

`--no-build`

Não compila o projeto de teste antes de sua execução. Também define o sinalizador `--no-restore` implicitamente.

`--no-restore`

Não executa uma restauração implícita ao executar o comando.

`-o|--output <OUTPUT_DIRECTORY>`

Diretório no qual encontram-se os binários para execução.

`-r|--results-directory <PATH>`

O diretório em que os resultados de teste serão colocados. Se o diretório especificado não existir, ele será criado.

`-s|--settings <SETTINGS_FILE>`

Configurações para usar ao executar testes.

`-t|--list-tests`

Lista todos os testes descobertos no projeto atual.

`-v|--verbosity <LEVEL>`

Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.

`RunSettings arguments`

Argumentos passados como configurações RunSettings para o teste. Os argumentos são especificados como pares `[name]=[value]` após "-- " (observe o espaço após --). Um espaço é usado para separar vários pares `[name]=[value]`.

Exemplo: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`

Para obter mais informações sobre RunSettings, confira [vstest.console.exe: Passando args de RunSettings](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

Usa os adaptadores de teste personalizado do caminho especificado na execução de teste.

`-c|--configuration {Debug|Release}`

Define a configuração da compilação. O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

Habilita o coletor de dados para a execução de teste. Para obter mais informações, consulte [Monitor and analyze test run](https://aka.ms/vstest-collect) (Monitorar e analisar a execução de teste).

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico para o arquivo especificado.

`-f|--framework <FRAMEWORK>`

Procura os binários de teste para uma [estrutura](../../standard/frameworks.md) específica.

`--filter <EXPRESSION>`

Filtra os testes no projeto atual usando a expressão especificada. Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details). Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).

`-h|--help`

Imprime uma ajuda breve para o comando.

`-l|--logger <LoggerUri/FriendlyName>`

Especifica um agente para resultados do teste.

`--no-build`

Não compila o projeto de teste antes de sua execução. Também define o sinalizador `--no-restore` implicitamente.

`--no-restore`

Não executa uma restauração implícita ao executar o comando.

`-o|--output <OUTPUT_DIRECTORY>`

Diretório no qual encontram-se os binários para execução.

`-r|--results-directory <PATH>`

O diretório em que os resultados de teste serão colocados. Se o diretório especificado não existir, ele será criado.

`-s|--settings <SETTINGS_FILE>`

Configurações para usar ao executar testes.

`-t|--list-tests`

Lista todos os testes descobertos no projeto atual.

`-v|--verbosity <LEVEL>`

Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

Usa os adaptadores de teste personalizado do caminho especificado na execução de teste.

`-c|--configuration {Debug|Release}`

Define a configuração da compilação. O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico para o arquivo especificado.

`-f|--framework <FRAMEWORK>`

Procura os binários de teste para uma [estrutura](../../standard/frameworks.md) específica.

`--filter <EXPRESSION>`

Filtra os testes no projeto atual usando a expressão especificada. Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details). Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).

`-h|--help`

Imprime uma ajuda breve para o comando.

`-l|--logger <LoggerUri/FriendlyName>`

Especifica um agente para resultados do teste.

`--no-build`

Não compila o projeto de teste antes de sua execução.

`-o|--output <OUTPUT_DIRECTORY>`

Diretório no qual encontram-se os binários para execução.

`-s|--settings <SETTINGS_FILE>`

Configurações para usar ao executar testes.

`-t|--list-tests`

Lista todos os testes descobertos no projeto atual.

`-v|--verbosity <LEVEL>`

Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.

---

## <a name="examples"></a>Exemplos

Execute os testes no projeto no diretório atual:

`dotnet test`

Execute os testes no projeto `test1`:

`dotnet test ~/projects/test1/test1.csproj`

Execute os testes no projeto no diretório atual e gere um arquivo de resultados de teste no formato trx:

`dotnet test --logger:trx`

## <a name="filter-option-details"></a>Filtrar detalhes da opção

`--filter <EXPRESSION>`

`<Expression>` tem o formato `<property><operator><value>[|&<Expression>]`.

`<property>` é um atributo de `Test Case`. A seguir estão as propriedades com suporte nas estruturas populares de teste de unidade:

| Estrutura de teste | Propriedades com suporte                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| MSTest         | <ul><li>FullyQualifiedName</li><li>Nome</li><li>ClassName</li><li>Prioridade</li><li>TestCategory</li></ul> |
| xUnit          | <ul><li>FullyQualifiedName</li><li>DisplayName</li><li>Características</li></ul>                                   |

O `<operator>` descreve a relação entre a propriedade o valor:

| Operador | Função        |
| :------: | --------------- |
| `=`      | Correspondência exata     |
| `!=`     | Sem correspondência exata |
| `~`      | Contém        |

`<value>` é uma cadeia de caracteres. As pesquisas não diferenciam maiúsculas de minúsculas.

Uma expressão sem um `<operator>` é automaticamente considerada como um `contains` na propriedade `FullyQualifiedName` (por exemplo, `dotnet test --filter xyz` é o mesmo que `dotnet test --filter FullyQualifiedName~xyz`).

As expressões podem ser associadas a operadores condicionais:

| Operador            | Função |
| ------------------- | -------- |
| <code>&#124;</code> | OU       |
| `&`                 | AND      |

Inclua expressões em parênteses ao usar operadores condicionais (por exemplo, `(Name~TestMethod1) | (Name~TestMethod2)`).

Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).

## <a name="see-also"></a>Consulte também

- [Estruturas e Destinos](../../standard/frameworks.md)
- [Catálogo do Identificador de Tempo de Execução do .NET Core](../rid-catalog.md)
