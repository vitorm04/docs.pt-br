---
title: Comando dotnet-restore | Microsoft Docs
description: "Saiba como restaurar as dependências e ferramentas específicas de projeto com o comando de dotnet restore"
keywords: dotnet-restore, CLI, comando da CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 10/07/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 60489b25-38de-47e6-bed1-59d9f42e2d46
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: df8174aa3252568d7112305af07e6399d96ca32f

---

#<a name="dotnet-restore"></a>dotnet-restore

> [!WARNING]
> Este tópico se aplica à Visualização 2 das Ferramentas do .NET Core. Para a versão do Ferramentas do .NET Core RC4, consulte o tópico [dotnet-restore (Ferramentas do .NET Core RC4)](../preview3/tools/dotnet-restore.md).

## <a name="name"></a>Nome

`dotnet-restore` – Restaura as dependências e as ferramentas de um projeto.

## <a name="synopsis"></a>Sinopse

`dotnet restore [root] [--help] [--force-english-output] [--source]  
    [--packages] [--disable-parallel] [--fallbacksource] [--configfile] 
    [--no-cache] [--infer-runtimes] [--verbosity] [--ignore-failed-sources]`

## <a name="description"></a>Descrição

O comando `dotnet restore` usa o NuGet para restaurar as dependências e ferramentas específicas de projeto que são especificadas no arquivo [project.json](project-json.md). Por padrão, a restauração das dependências e ferramentas são feitas em paralelo.

Para restaurar as dependências, o NuGet precisa dos feeds de onde se encontram os pacotes. Os feeds geralmente são fornecidos por meio do arquivo de configuração NuGet; um padrão um está presente quando as ferramentas da CLI são instaladas. Você pode especificar mais feeds criando seu próprio arquivo NuGet.config no diretório do projeto. Os feeds também podem ser especificados por invocação no prompt de comando. 

Para dependências, você pode especificar onde os pacotes restaurados são colocados durante a operação de restauração usando o argumento `--packages`. Se não for especificado, o cache do pacote NuGet padrão será usado. Ele é encontrado no diretório `.nuget/packages` do diretório base do usuário em todos os sistemas operacionais (por exemplo, */home/user1* no Linux ou *C:\Usuários\user1* no Windows).

Para ferramentas específicas do projeto, o `dotnet restore` primeiro restaura o pacote no qual a ferramenta foi empacotada e prossegue com a restauração das dependências da ferramenta conforme especificado no seu [project.json](project-json.md). 

## <a name="options"></a>Opções

`[root]` 
    
 Uma lista de projetos ou pastas de projeto para restaurar. Cada valor pode ser um caminho para um arquivo [project.json](project-json.md), [global.json](global-json.md) ou para uma pasta. Se uma pasta for especificada, a operação de restauração pesquisará recursivamente um arquivo [project.json](project-json.md) em todos os subdiretórios e restaurações para cada arquivo [project.json](project-json.md) encontrado.

`-h|--help`

Imprime uma ajuda breve para o comando.

 `--force-english-output`

Força a execução do aplicativo usando uma cultura invariável com base em inglês.

`-s|--source <SOURCE>`

Especifica uma origem de pacote NuGet a ser usada durante a operação de restauração. Isso substitui todas as fontes especificadas nos arquivos NuGet.config. Diversas fontes podem ser fornecidas especificando essa opção várias vezes.

`--packages <PACKAGES_DIRECTORY]`

Especifica o diretório no qual os pacotes restaurados serão colocados. 

`--disable-parallel`

Desabilita a restauração de vários projetos paralelamente. 

`-f|--fallbacksource <FEED>`

Especifica uma lista das origens de pacotes para usar como um fallback na operação de restauração se todas as demais fontes falharem. Todos os formatos de feed válidos são permitidos. Diversas fontes de fallback podem ser fornecidas especificando essa opção várias vezes.

`--configfile <FILE>`

O arquivo de configuração NuGet (NuGet.config) a ser usado para a operação de restauração.

`--no-cache`

Especifica para não armazenar os pacotes e solicitações HTTP em cache.

`--infer-runtimes`

Opção temporária para permitir que o NuGet infira nos RIDs (Identificadores de Tempo de Execução) para repositórios herdados.

`--verbosity [LEVEL]`

O detalhamento do log a ser usado. Valores permitidos: `Debug`, `Verbose`, `Information`, `Minimal`, `Warning` ou `Error`.

` --ignore-failed-sources`

Somente avise sobre fontes com falha se houver pacotes que cumprem o requisito de versão.

## <a name="examples"></a>Exemplos

Restaure as dependências e as ferramentas para o projeto no diretório atual:

`dotnet restore` 

Restaure as dependências e as ferramentas para o projeto `app1` encontrado no caminho fornecido:

`dotnet restore ~/projects/app1/project.json`
    
Restaure as dependências e as ferramentas para o projeto no diretório atual usando o caminho de arquivo fornecido como a fonte de fallback:

`dotnet restore -f c:\packages\mypackages` 

Restaure as dependências e as ferramentas para o projeto no diretório atual usando os dois caminhos de arquivo fornecidos como fontes de fallback:

`dotnet restore -f c:\packages\mypackages -f c:\packages\myotherpackages` 

Restaure as dependências e as ferramentas para o projeto no diretório atual, mostrando apenas os erros na saída:

`dotnet restore --verbosity Error`


<!--HONumber=Feb17_HO2-->


