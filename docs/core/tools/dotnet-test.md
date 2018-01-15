---
title: "Comando dotnet test – CLI do .NET Core"
description: "O comando dotnet test é usado para executar testes de unidade em um determinado projeto."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: fac5e3cb602f6dc5c06b1b29e9924ce4be7ae273
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-test"></a>dotnet test

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nome

`dotnet test` - driver de teste do .NET usado para executar testes de unidade.

## <a name="synopsis"></a>Sinopse

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)


```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]
dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]
dotnet test [-h|--help]
```
---

## <a name="description"></a>Descrição

O comando `dotnet test` é usado para executar testes de unidade em um determinado projeto. Testes de unidade são projetos de aplicativo de console que têm dependências na estrutura de teste da unidade (por exemplo, MSTest, NUnit ou xUnit) e no executor de teste dotnet da estrutura de teste de unidade. Eles são empacotados como pacotes NuGet e são restaurados como dependências comuns para o projeto.

Projetos de teste também precisam especificar o executor de teste. Isso é especificado usando um elemento comum `<PackageReference>`, conforme mostrado no exemplo de arquivo de projeto a seguir:

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a>Arguments

`PROJECT`

Especifica um caminho para o projeto de teste. Se for omitido, o padrão será o diretório atual.

## <a name="options"></a>Opções

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

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

Filtra os testes no projeto atual usando a expressão especificada. Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details). Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executar testes de unidade seletivos](../testing/selective-unit-tests.md).

`-h|--help`

Imprime uma ajuda breve para o comando.

`-l|--logger <LoggerUri/FriendlyName>`

Especifica um agente para resultados do teste.

`--no-build`

Não compila o projeto de teste antes de executá-lo.

`--no-restore`

Não executa uma restauração implícita ao executar o comando.

`-o|--output <OUTPUT_DIRECTORY>`

Diretório no qual encontram-se os binários para execução.

`-r|--results-directory <PATH>`

O diretório em que os resultados de teste serão colocados. O diretório especificado será criado se ele não existir.

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

Filtra os testes no projeto atual usando a expressão especificada. Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details). Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executar testes de unidade seletivos](../testing/selective-unit-tests.md).

`-h|--help`

Imprime uma ajuda breve para o comando.

`-l|--logger <LoggerUri/FriendlyName>`

Especifica um agente para resultados do teste.

`--no-build`

Não compila o projeto de teste antes de executá-lo.

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

## <a name="filter-option-details"></a>Filtrar detalhes da opção

`--filter <EXPRESSION>`

`<Expression>` tem o formato `<property><operator><value>[|&<Expression>]`.

`<property>` é um atributo de `Test Case`. A seguir estão as propriedades com suporte nas estruturas populares de teste de unidade:

| Estrutura de teste | Propriedades com suporte                                                                                      |
| :------------: | --------------------------------------------------------------------------------------------------------- |
| MSTest         | <ul><li>FullyQualifiedName</li><li>Nome</li><li>ClassName</li><li>Prioridade</li><li>TestCategory</li></ul> |
| Xunit          | <ul><li>FullyQualifiedName</li><li>DisplayName</li><li>Características</li></ul>                                   |

O `<operator>` descreve a relação entre a propriedade o valor:

| Operador | Função        |
| :------: | --------------- |
| `=`      | Correspondência exata     |
| `!=`     | Sem correspondência exata |
| `~`      | Contém        |

`<value>` é uma cadeia de caracteres. As pesquisas não diferenciam maiúsculas de minúsculas.

Uma expressão sem um `<operator>` é automaticamente considerada como um `contains` na propriedade `FullyQualifiedName` (por exemplo, `dotnet test --filter xyz` é o mesmo que `dotnet test --filter FullyQualifiedName~xyz`).

As expressões podem ser associadas a operadores condicionais:

| Operador | Função |
| :------: | :------: |
| <code>&#124;</code>      | OU       |
| `&`      | AND      |

Inclua expressões em parênteses ao usar operadores condicionais (por exemplo, `(Name~TestMethod1) | (Name~TestMethod2)`).

Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executar testes de unidade seletivos](../testing/selective-unit-tests.md).

## <a name="see-also"></a>Consulte também

 [Estruturas e Destinos](../../standard/frameworks.md)  
 [Catálogo do Identificador de Tempo de Execução do .NET Core](../rid-catalog.md)
