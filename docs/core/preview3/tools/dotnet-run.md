---
title: Comando dotnet-run | Microsoft Docs
description: "O comando dotnet-run fornece uma opção conveniente para executar o aplicativo do código-fonte."
keywords: dotnet-run, CLI, comando da CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 10/07/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 40d4e60f-9900-4a48-b03c-0bae06792d91
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: 3f9d50dcc58ad4af836a6b19d8daf7bb6bf60341

---

#<a name="dotnet-run-net-core-tools-rc4"></a>dotnet-run (Ferramentas do .NET Core RC4)

> [!WARNING]
> Este tópico se aplica às Ferramentas do .NET Core RC4. Para a versão da Visualização 2 das Ferramentas do .NET Core, consulte o tópico [dotnet-run](../../tools/dotnet-run.md).

## <a name="name"></a>Nome 

dotnet-run – Executa o código-fonte “in-loco” sem qualquer comando de compilação ou inicialização explícito.

## <a name="synopsis"></a>Sinopse

`dotnet run [--help] [--framework] [--configuration]
    [--project] [[--] [application arguments]]`

## <a name="description"></a>Descrição
O comando `dotnet run` fornece uma opção conveniente para executar o aplicativo do código-fonte com um comando. Ele compila o código-fonte, gera um programa de saída e executa o programa. Esse comando é útil para desenvolvimento iterativo rápido e também pode ser usado para executar um programa fonte distribuída (por exemplo, um site).

Esse comando se baseia no [dotnet build](dotnet-build.md) para criar entradas de origem para um assembly do .NET antes de iniciar o programa. Os requisitos desse comando e o tratamento das entradas de fonte são herdados do comando build. A documentação para o comando de build fornece mais informações sobre esses requisitos.

Arquivos de saída são gravados na pasta *bin* filho, que será criada se não existir. Os arquivos serão substituídos conforme necessário. Arquivos temporários são gravados para a pasta *obj* filho.  

No caso de um projeto com várias estruturas especificadas, o `dotnet run` selecionará as estruturas do .NET Core primeiramente. Se elas não existirem, ocorrerá um erro. Para especificar outras estruturas, use o argumento `--framework`.

O comando `dotnet run` deve ser usado no contexto de projetos, não assemblies compilados. Se você estiver tentando executar um DLL de aplicativo portátil em vez disso, deverá usar [dotnet](dotnet.md) sem nenhum comando, como no exemplo a seguir:
 
`dotnet myapp.dll`

Para obter mais informações sobre o driver `dotnet`, consulte o tópico [CLI (Ferramentas de Linha de Comando) do .NET Core](index.md).

## <a name="options"></a>Opções

`--`

Delimita os argumentos para `dotnet run` dos argumentos para o aplicativo que está sendo executado. Todos os argumentos depois desse serão passados para o aplicativo que está sendo executado. 

`-h|--help`

Imprime uma ajuda breve para o comando.

`-f`, `--framework <FRAMEWORK_IDENTIFIER>`

Executa o aplicativo para um determinado FID (Identificador de Estrutura). 

`-c`, `--configuration <Debug|Release>`

Configuração a ser usada durante a publicação. O valor padrão é `Debug`.

`-p`, `--project [PATH]`

Especifica qual projeto deve ser executado. Ele pode ser um caminho para um arquivo [csproj](csproj.md) ou para um diretório que contém um arquivo [csproj](csproj.md). Se não for especificado, o padrão será o diretório atual. 

## <a name="examples"></a>Exemplos

Execute o projeto no diretório atual: `dotnet run` 

Execute o projeto especificado:

`dotnet run --project /projects/proj1/proj1.csproj`

Execute o projeto no diretório atual (o argumento `--help` neste exemplo é passado para o aplicativo que está sendo executado, visto que o argumento `--` foi usado):

`dotnet run --configuration Release -- --help`


<!--HONumber=Feb17_HO2-->


