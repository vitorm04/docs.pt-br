---
title: Comando dotnet | SDK do .NET Core
description: "Saiba mais sobre o comando dotnet (o driver genérico para as ferramentas da CLI do .NET Core) e seu uso."
keywords: dotnet, CLI, comandos da CLI, .NET Core
author: mairaw
manager: wpickett
ms.date: 10/07/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 93015521-2127-4fe9-8fce-ca79bcc4ff49
translationtype: Human Translation
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: bbc13c8cca82e660f0f8ccf7d88c0340d9c06e68

---

#<a name="dotnet-command"></a>Comando dotnet

## <a name="name"></a>Nome

dotnet – Driver geral para executar os comandos da linha de comando

## <a name="synopsis"></a>Sinopse

`dotnet [--version] [--verbose] [--info] [command] [arguments] [--help]`

## <a name="description"></a>Descrição
`dotnet` é um driver genérico para a cadeia de ferramentas da CLI (Interface de Linha de Comando). Invocado por conta própria, ele fornecerá breve instruções de uso. 

Cada recurso específico é implementado como um comando. Para usar o recurso, o comando é especificado após `dotnet`, como [`dotnet build`](dotnet-build.md). Todos os argumentos após o comando são seus próprios argumentos. 

A única vez que `dotnet` é usado como um comando em si é ao executar aplicativos portáteis. Basta especificar um DLL de aplicativo portátil após o verbo `dotnet` para executar o aplicativo.    

## <a name="options"></a>Opções

`-v|--verbose`

Habilita a saída detalhada.

`--version`

Imprime a versão das ferramentas de CLI.

`--info`

Imprime informações mais detalhadas sobre as ferramentas de CLI, como o sistema operacional atual, para confirmar SHA para a versão, etc. 

`-h|--help`

Imprime uma ajuda breve para o comando. Se estiver usando apenas `dotnet`, ele também imprimirá uma lista de comandos disponíveis.  

## <a name="dotnet-commands"></a>Comandos dotnet

Os comandos a seguir existem para dotnet:

* [dotnet-new](dotnet-new.md)
   * Inicializa um projeto de aplicativo de console C# ou F#.
* [dotnet-restore](dotnet-restore.md)
  * Restaura as dependências para um determinado aplicativo. 
* [dotnet-build](dotnet-build.md)
  * Compila um aplicativo .NET Core.
* [dotnet-publish](dotnet-publish.md)
   * Publica um aplicativo portátil ou autocontido .NET.
* [dotnet-run](dotnet-run.md)
   * Executa o aplicativo na origem.
* [dotnet-test](dotnet-test.md)
   * Executa testes usando um executor de testes especificado no project.json.
* [dotnet-pack](dotnet-pack.md)
   * Cria um pacote NuGet do seu código.
* [dotnet-migrate](dotnet-migrate.md)
   * Migra um projeto de Visualização 2 válido para um projeto de Visualização 3
* [dotnet-msbuild](dotnet-msbuild.md)
   * Oferece acesso à linha de comando do MSBuild

## <a name="examples"></a>Exemplos

Inicialize um aplicativo de console .NET Core de exemplo que pode ser compilado e executado:

`dotnet new`

Restaure as dependências para um determinado aplicativo:

`dotnet restore`

Compile um projeto e suas dependências em um determinado diretório: 

`dotnet build`

Execute um aplicativo portátil chamado `myapp.dll`: `dotnet myapp.dll`

## <a name="environment"></a>Ambiente 

`DOTNET_PACKAGES`

O cache do pacote principal. Se não for definido, o padrão será $HOME/.nuget/packages em Unix ou %HOME%\NuGet\Packages no Windows.

`DOTNET_SERVICING`

Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o tempo de execução.

`DOTNET_CLI_TELEMETRY_OPTOUT`

Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft. `true` para recusar o recurso de telemetria (valores verdadeiro, 1 ou sim aceito); caso contrário, `false` (valores falso, 0 ou não aceito). Se não estiver definido, o padrão será `false`, ou seja, o recurso de telemetria é ativado.




<!--HONumber=Nov16_HO3-->


