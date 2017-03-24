---
title: Comando dotnet-run | Microsoft Docs
description: "O comando dotnet-run fornece uma opção conveniente para executar o aplicativo do código-fonte."
keywords: dotnet-run, CLI, comando da CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 40d4e60f-9900-4a48-b03c-0bae06792d91
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 60bb9160e43788539b0dc6bcf1372bb925e9ba22
ms.lasthandoff: 03/07/2017

---

#<a name="dotnet-run"></a>dotnet-run

## <a name="name"></a>Nome 

`dotnet-run` – Executa o código-fonte “in-loco” sem qualquer comando de compilação ou inicialização explícito.

## <a name="synopsis"></a>Sinopse

```
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```

## <a name="description"></a>Descrição

O comando `dotnet run` fornece uma opção conveniente para executar o aplicativo do código-fonte com um comando. Ele é útil para o desenvolvimento iterativo rápido na linha de comando. O comando depende do comando [`dotnet build`](dotnet-build.md) para compilar o código; portanto, os requisitos do build, como o requisito de que o projeto deve ser restaurado primeiro, se aplicam também a `dotnet run`. 

Os arquivos de saída são gravados no local padrão, que é `bin/<configuration>/<target>`. Por exemplo, se você tiver um aplicativo `netcoreapp1.0` e executar `dotnet run`, a saída será colocada em `bin/Debug/netcoreapp1.0`. Os arquivos são substituídos conforme necessário. Os arquivos temporários são colocados no diretório `obj`. 

No caso de um projeto com várias estruturas especificadas, `dotnet run` mostrará um erro, a menos que a opção `--framework` seja usada para especificar em qual estrutura o aplicativo deverá ser executado.

O comando `dotnet run` deve ser usado no contexto de projetos, não assemblies compilados. Se você estiver tentando executar um DLL de aplicativo portátil em vez disso, deverá usar [dotnet](dotnet.md) sem nenhum comando, como no exemplo a seguir:
 
`dotnet myapp.dll`

Para obter mais informações sobre o driver `dotnet`, consulte o tópico [CLI (Ferramentas de Linha de Comando) do .NET Core](index.md).

Para executar o aplicativo, o comando `dotnet run` resolve as dependências do aplicativo que estão fora do tempo de execução compartilhado do cache NuGet. Por esse motivo, não é recomendável usar esse comando para executar aplicativos em produção. Em vez disso, é necessário [criar uma implantação](../deploying/index.md) usando o comando [`dotnet publish`](dotnet-publish.md) e usá-la na produção. 

## <a name="options"></a>Opções

`--`

Delimita os argumentos para `dotnet run` dos argumentos para o aplicativo que está sendo executado. Todos os argumentos depois desse serão passados para o aplicativo que está sendo executado. 

`-h|--help`

Imprime uma ajuda breve para o comando.

`-c|--configuration {Debug|Release}`

Configuração a ser usada ao compilar o projeto. O valor padrão é `Debug`.

`-f|--framework <FRAMEWORK_IDENTIFIER>`

Compila e executa o aplicativo usando a estrutura especificada. A estrutura deve ser especificada no arquivo de projeto.

`-p|--project <PATH>`

Especifica o caminho para o arquivo de projeto a ser executado. Ele pode ser um caminho para um arquivo [csproj](csproj.md) ou para um diretório que contém um arquivo [csproj](csproj.md). Se não for especificado, o padrão será o diretório atual. 

## <a name="examples"></a>Exemplos

Execute o projeto no diretório atual:

`dotnet run` 

Execute o projeto especificado:

`dotnet run --project /projects/proj1/proj1.csproj`

Execute o projeto no diretório atual (o argumento `--help` neste exemplo é passado para o aplicativo que está sendo executado, visto que o argumento `--` foi usado):

`dotnet run --configuration Release -- --help`
