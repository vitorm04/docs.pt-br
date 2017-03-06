---
title: Comando dotnet-test | Microsoft Docs
description: "O comando `dotnet test` é usado para executar testes de unidade em um determinado projeto."
keywords: dotnet-test, CLI, comando da CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 10/07/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 3a0fa917-eb0a-4d7e-9217-d06e65455675
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: 871a6f736272309f6fae74b06f437c7271df2321

---

#<a name="dotnet-test"></a>dotnet-test

> [!WARNING]
> Este tópico se aplica à Visualização 2 das Ferramentas do .NET Core. Para a versão do Ferramentas do .NET Core RC4, consulte o tópico [dotnet-test (Ferramentas do .NET Core RC4)](../preview3/tools/dotnet-test.md).

## <a name="name"></a>Nome

`dotnet-test` – Executa testes de unidade usando o executor de teste configurado.

## <a name="synopsis"></a>Sinopse

`dotnet test [project] [--help] 
    [--parentProcessId] [--port] [--configuration]   
    [--output] [--build-base-path] [--framework] [--runtime]
    [--no-build]`  

## <a name="description"></a>Descrição

O comando `dotnet test` é usado para executar testes de unidade em um determinado projeto. Testes de unidade são projetos de biblioteca de classes que têm dependências na estrutura de teste da unidade (por exemplo, NUnit ou xUnit) e o executor de teste dotnet dessa estrutura de teste de unidade. Eles são empacotados como pacotes NuGet e são restaurados como dependências comuns para o projeto.

Projetos de teste também precisam especificar uma propriedade de executor de teste no project.json usando o nó “testRunner”. Esse valor deve conter o nome da estrutura de teste de unidade.

O project.json de exemplo a seguir mostra as propriedades necessárias:

```json
{
  "version": "1.0.0-*",
  "buildOptions": {
    "debugType": "portable"
  },
  "dependencies": {
    "System.Runtime.Serialization.Primitives": "4.1.1",
    "xunit": "2.1.0",
    "dotnet-test-xunit": "1.0.0-rc2-192208-24"
  },
  "testRunner": "xunit",
  "frameworks": {
    "netcoreapp1.0": {
      "dependencies": {
        "Microsoft.NETCore.App": {
          "type": "platform",
          "version": "1.0.0"
        }
      },
      "imports": [
        "dotnet5.4",
        "portable-net451+win8"
      ]
    }
  }
}
```

`dotnet test` dá suporte a dois modos de execução:

1. Console: no modo de console, o `dotnet test` apenas executa totalmente qualquer comando passado para ele e gera os resultados. Sempre que você invocar `dotnet test` sem passar --port, ele é executado no modo de console, que por sua vez fará com que o executor seja executado no modo de console.
2. Tempo de design: usado no contexto de outras ferramentas, como editores ou IDEs (ambientes de desenvolvimento integrado). Você pode encontrar mais informações sobre esse modo no documento [protocolo dotnet-test](test-protocol.md). 

## <a name="options"></a>Opções

`[project]`
    
Especifica um caminho para o projeto de teste. Se for omitido, o padrão será o diretório atual.

`-?|-h|--help`

Imprime uma ajuda breve para o comando.

`--parentProcessId`

Usado pelos IDEs para especificar sua ID de processo. O teste será fechado se o processo-pai também o for.

`--port`

Usado pelos IDEs para especificar um número da porta para escutar uma conexão.

`-c|--configuration <Debug|Release>`

Configuração de build. O valor padrão é `Release`. 

`-o|--output [OUTPUT_DIRECTORY]`

Diretório no qual encontram-se os binários para execução.

`-b|--build-base-path <OUTPUT_DIRECTORY>`

Diretório no qual as saídas temporárias são colocadas.

`-f|--framework [FRAMEWORK]`

Procura os binários de teste para uma estrutura específica.

`-r|--runtime [RUNTIME_IDENTIFIER]`

Procure os binários de teste para o tempo de execução especificado.

`--no-build` 

Não compila o projeto de teste antes de executá-lo. 

## <a name="examples"></a>Exemplos

Execute os testes no projeto no diretório atual:

`dotnet test` 

Execute os testes no projeto test1:

`dotnet test /projects/test1/project.json` 

## <a name="see-also"></a>Consulte também

[Protocolo de comunicação dotnet-test](test-protocol.md)

[Estruturas](../../standard/frameworks.md)

[Catálogo de RID (Identificador de Tempo de Execução)](../rid-catalog.md)


<!--HONumber=Feb17_HO2-->


