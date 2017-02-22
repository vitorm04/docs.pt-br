---
title: Comando dotnet-test | Microsoft Docs
description: "O comando `dotnet test` é usado para executar testes de unidade em um determinado projeto."
keywords: dotnet-test, CLI, comando da CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 02/08/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 4bf0aef4-148a-41c6-bb95-0a9e1af8762e
translationtype: Human Translation
ms.sourcegitcommit: 02f39bc959a56ab0fc2cfa57ce13f300a8a46107
ms.openlocfilehash: 204ebdb5a945dcd0c9277f1d95c113e829303b32

---

#<a name="dotnet-test-net-core-tools-rc4"></a>dotnet-test (Ferramentas do .NET Core RC4)

> [!WARNING]
> Este tópico se aplica às Ferramentas do .NET Core RC4. Para a versão de Visualização 2 das Ferramentas do .NET Core, consulte o tópico [dotnet-test](../../tools/dotnet-test.md).

## <a name="name"></a>Nome

`dotnet-test` – Driver de teste .NET

## <a name="synopsis"></a>Sinopse

`dotnet test [project] [--help] 
    [--settings] [--list-tests] [--filter] 
    [--test-adapter-path] [--logger] 
    [--configuration] [--framework] [--output] [--diag]
    [--no-build] [--verbosity]`

## <a name="description"></a>Descrição

O comando `dotnet test` é usado para executar testes de unidade em um determinado projeto. Testes de unidade são projetos de biblioteca de classes que têm dependências na estrutura de teste da unidade (por exemplo, NUnit ou xUnit) e o executor de teste dotnet dessa estrutura de teste de unidade. Eles são empacotados como pacotes NuGet e são restaurados como dependências comuns para o projeto.

Projetos de teste também precisam especificar o executor de teste. Isso é especificado usando um elemento comum `<PackageReference>`, conforme mostrado no exemplo de arquivo de projeto a seguir:

[!code-xml[Modelo Básico do XUnit](../../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="options"></a>Opções

`[project]`
    
Especifica um caminho para o projeto de teste. Se for omitido, o padrão será o diretório atual.

`-h|--help`

Imprime uma ajuda breve para o comando.

`-s|--settings <SETTINGS_FILE>`

Configurações para usar ao executar testes. 

`-t|--list-tests`

Lista todos os testes descobertos no projeto atual. 

`--filter <EXPRESSION>`

Filtra os testes no projeto atual usando a expressão especificada. Para saber mais sobre o suporte à filtragem, consulte [Executar testes seletivos de unidade no Visual Studio usando o TestCaseFilter](https://aka.ms/vstest-filtering).

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

Usa os adaptadores de teste personalizado do caminho especificado na execução de teste. 

`-l|--logger <LoggerUri/FriendlyName>`

Especifica um agente para resultados do teste. 

`-c|--configuration <Debug|Release>`

Configuração de build. O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.

`-f|--framework <FRAMEWORK>`

Procura os binários de teste para uma estrutura específica.

`-o|--output <OUTPUT_DIRECTORY>`

Diretório no qual encontram-se os binários para execução.

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico para o arquivo especificado. 

`--no-build` 

Não compila o projeto de teste antes de executá-lo.

`-v|--verbosity [quiet|minimal|normal|diagnostic]`

Defina o nível de detalhamento do comando. Você pode especificar os seguintes níveis de detalhamento: quiet, minimal, normal, detailed e diagnóstico. 

## <a name="examples"></a>Exemplos

Execute os testes no projeto no diretório atual:

`dotnet test` 

Execute os testes no projeto test1:

`dotnet test ~/projects/test1/test1.csproj` 

## <a name="see-also"></a>Consulte também

[Estruturas](../../../standard/frameworks.md)

[Catálogo de RID (Identificador de Tempo de Execução)](../../rid-catalog.md)



<!--HONumber=Feb17_HO2-->


