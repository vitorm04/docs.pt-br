---
title: Comando dotnet-test - CLI do .NET Core | Microsoft Docs
description: "O comando `dotnet test` é usado para executar testes de unidade em um determinado projeto."
keywords: dotnet-test, CLI, comando da CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 03/25/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 4bf0aef4-148a-41c6-bb95-0a9e1af8762e
ms.translationtype: Human Translation
ms.sourcegitcommit: ae036cfcad341ffc859336a7ab2a49feec145715
ms.openlocfilehash: 734cf337fdd0d33f6c2b6d929b795b2307135550
ms.contentlocale: pt-br
ms.lasthandoff: 05/18/2017

---

#<a name="dotnet-test"></a>dotnet-test

## <a name="name"></a>Nome

`dotnet-test` - driver de teste do .NET usado para executar testes de unidade.

## <a name="synopsis"></a>Sinopse

`dotnet test [<PROJECT>] [-s|--settings] [-t|--list-tests] [--filter] [-a|--test-adapter-path] [-l|--logger] [-c|--configuration] [-f|--framework] [-o|--output] [-d|--diag] [--no-build] [-v|--verbosity] [-h|--help]`

## <a name="description"></a>Descrição

O comando `dotnet test` é usado para executar testes de unidade em um determinado projeto. Testes de unidade são projetos de aplicativo de console que têm dependências na estrutura de teste da unidade (por exemplo, MSTest, NUnit ou xUnit) e no executor de teste dotnet da estrutura de teste de unidade. Eles são empacotados como pacotes NuGet e são restaurados como dependências comuns para o projeto.

Projetos de teste também precisam especificar o executor de teste. Isso é especificado usando um elemento comum `<PackageReference>`, conforme mostrado no exemplo de arquivo de projeto a seguir:

[!code-xml[Modelo Básico do XUnit](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="options"></a>Opções

`PROJECT`
    
Especifica um caminho para o projeto de teste. Se for omitido, o padrão será o diretório atual.

`-h|--help`

Imprime uma ajuda breve para o comando.

`-s|--settings <SETTINGS_FILE>`

Configurações para usar ao executar testes. 

`-t|--list-tests`

Lista todos os testes descobertos no projeto atual. 

`--filter <EXPRESSION>`

Filtra os testes no projeto atual usando a expressão especificada. Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details). Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executar testes de unidade seletivos](../testing/selective-unit-tests.md).

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

Usa os adaptadores de teste personalizado do caminho especificado na execução de teste. 

`-l|--logger <LoggerUri/FriendlyName>`

Especifica um agente para resultados do teste. 

`-c|--configuration <CONFIGURATION>`

Configuração de build. O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.

`-f|--framework <FRAMEWORK>`

Procura os binários de teste para uma [estrutura](../../standard/frameworks.md) específica.

`-o|--output <OUTPUT_DIRECTORY>`

Diretório no qual encontram-se os binários para execução.

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico para o arquivo especificado. 

`--no-build` 

Não compila o projeto de teste antes de executá-lo.

`-v|--verbosity <LEVEL>`

Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.

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
| `|`      | OU       |
| `&`      | AND      |

Você pode incluir expressões em parênteses ao usar operadores condicionais (por exemplo: `(Name~TestMethod1) | (Name~TestMethod2)`).

Para obter informações e exemplos adicionais sobre como usar a filtragem de teste de unidade seletivo, confira [Executar testes de unidade seletivos](../testing/selective-unit-tests.md).

## <a name="see-also"></a>Consulte também

[Estruturas e Destinos](../../standard/frameworks.md)   
[Catálogo do Identificador de Tempo de Execução do .NET Core](../rid-catalog.md)

