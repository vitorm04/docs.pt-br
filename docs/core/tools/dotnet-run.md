---
title: "Comando dotnet-run – CLI do .NET Core"
description: "O comando dotnet-run fornece uma opção conveniente para executar o aplicativo do código-fonte."
keywords: dotnet-run, CLI, comando da CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 03/22/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 40d4e60f-9900-4a48-b03c-0bae06792d91
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f0a6fce4f83808076b7cbcabdaa948badde2cf80
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-run"></a>dotnet-run

## <a name="name"></a>Nome 

`dotnet-run` – Executa o código-fonte sem qualquer comando de compilação ou inicialização explícito.

## <a name="synopsis"></a>Sinopse

`dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]] [-h|--help]`

## <a name="description"></a>Descrição

O comando `dotnet run` fornece uma opção conveniente para executar o aplicativo do código-fonte com um comando. Ele é útil para o desenvolvimento iterativo rápido a partir da linha de comando. O comando depende do comando [`dotnet build`](dotnet-build.md) para compilar o código. Os requisitos para a compilação, como o projeto, devem ser restaurado primeiro, e se aplicam a `dotnet run` também. 

Os arquivos de saída são gravados no local padrão, que é `bin/<configuration>/<target>`. Por exemplo, se você tiver um aplicativo `netcoreapp1.0` e executar `dotnet run`, a saída será colocada em `bin/Debug/netcoreapp1.0`. Os arquivos são substituídos conforme necessário. Os arquivos temporários são colocados no diretório `obj`. 

Se o projeto especificar várias estruturas, a execução de `dotnet run` resultará em um erro, a menos que a opção `-f|--framework <FRAMEWORK>` seja usada para especificar a estrutura.

O comando `dotnet run` é usado no contexto de projetos, não assemblies compilados. Se, em vez disso, você estiver tentando executar uma DLL de aplicativo dependente da estrutura, use [dotnet](dotnet.md) sem um comando. Por exemplo, para executar `myapp.dll`, use:
 
```
dotnet myapp.dll
```

Para saber mais sobre o driver `dotnet`, veja o tópico [CLI (Ferramentas de Linha de Comando) do .NET Core](index.md).

Para executar o aplicativo, o comando `dotnet run` resolve as dependências do aplicativo que estão fora do tempo de execução compartilhado do cache NuGet. Como ele usa as dependências em cache, não recomendamos usar `dotnet run` para executar aplicativos em produção. Em vez disso, [crie uma implantação](../deploying/index.md) usando o comando [`dotnet publish`](dotnet-publish.md) e implante a saída publicada. 

## <a name="options"></a>Opções

`--`

Delimita os argumentos para `dotnet run` dos argumentos para o aplicativo que está sendo executado. Todos os argumentos depois desse serão passados para o aplicativo que está sendo executado. 

`-h|--help`

Imprime uma ajuda breve para o comando.

`-c|--configuration <CONFIGURATION>`

Configuração a ser usada ao compilar o projeto. O valor padrão é `Debug`.

`-f|--framework <FRAMEWORK>`

Compila e executa o aplicativo usando a [estrutura](../../standard/frameworks.md) especificada. A estrutura deve ser especificada no arquivo de projeto.

`-p|--project <PATH/PROJECT.csproj>`

Especifica o caminho e o nome do arquivo de projeto. (Consulte a OBSERVAÇÃO.) Se não for especificado, o padrão será o diretório atual.

> [!NOTE]
> Use o caminho e o nome do arquivo de projeto com a opção `-p|--project`. Uma regressão na CLI impede o fornecimento de um caminho de pasta no momento. Para saber mais e controlar esse problema, confira [dotnet run -p, não é possível iniciar um projeto (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).

## <a name="examples"></a>Exemplos

Execute o projeto no diretório atual:

`dotnet run` 

Execute o projeto especificado:

`dotnet run --project /projects/proj1/proj1.csproj`

Execute o projeto no diretório atual (o argumento `--help` neste exemplo é passado para o aplicativo, visto que o argumento `--` foi usado):

`dotnet run --configuration Release -- --help`

