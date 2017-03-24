---
title: Comando dotnet-migrate | Microsoft Docs
description: "O comando dotnet-migrate migra um projeto e todas as suas dependências."
keywords: dotnet-migrate, CLI, comando da CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 0da07253-5ae1-42e9-9455-bffee9950952
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: b7da4df5319e7c17900b9c093347e8a17045a6a3
ms.lasthandoff: 03/07/2017

---
#<a name="dotnet-migrate"></a>dotnet-migrate

## <a name="name"></a>Nome 
dotnet-migrate – migra um projeto do .NET Core Visualização 2 para um projeto do SDK 1.0 do .NET Core.

## <a name="synopsis"></a>Sinopse

```
dotnet migrate [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file] [-s|--skip-project-references] [-r|--report-file] [--format-report-file-json] [--skip-backup] [<arguments>]
dotnet migrate [-h|--help]
```

## <a name="description"></a>Descrição

O comando `dotnet migrate` migrará um projeto válido baseado em *project.json* da Visualização 2 para um projeto válido baseado em *csproj* do SDK 1.0 do .NET Core. 

Por padrão, o comando migrará o projeto raiz e as referências de projeto que o projeto raiz contém. Esse comportamento pode ser desabilitado usando a opção `--skip-project-references` no tempo de execução. 

A migração pode ser feita em:

* Um único projeto, especificando o arquivo *project.json* a ser migrado
* Todos os diretórios especificados no arquivo *global.json*, passando um caminho para o arquivo *global.json*
* Em todos os subdiretórios do diretório especificado, recursivamente 

O comando de migração manterá o arquivo *project.json* migrado em um diretório `backup`, que será criado se ainda não existir. Isso pode ser substituído usando a opção `--skip-backup`. 

Por padrão, a operação de migração produzirá o estado do processo de migração para a saída padrão (STDOUT). Se você usar a opção `--report-file`, essa saída também será salva em um arquivo que você especificar. 

O comando `dotnet migrate` dá suporte apenas a arquivos *project.json* válidos da Visualização 2. Isso significa que não é possível usá-lo para migrar um DNX antigo ou arquivos *project.json* da Visualização 1 diretamente para csproj; primeiro, é necessário migrá-los para os arquivos project.json da Visualização 2 e, em seguida, para os arquivos csproj. No futuro, haverá suporte para projetos da Visualização 1. 

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.  

`-t|--template-file <TEMPLATE_FILE>`

Arquivo csproj de modelo a ser usado para migração. Por padrão, o mesmo modelo removido pelo `dotnet new console` será usado. 

`-v|--sdk-package-version <VERSION>`

A versão do pacote do sdk que será referenciado no aplicativo migrado. O padrão é a versão do sdk no novo dotnet.

`-x|--xproj-file <FILE>`

O caminho para o arquivo xproj a ser usado. Necessário quando há mais de um xproj em um diretório do projeto.

`-s|--skip-project-references [Debug|Release]`

Ignorar referências de projeto migradas. Por padrão, as referências de projeto são migradas recursivamente.

`-r|--report-file <REPORT_FILE>`

Relatório de migração de saída em um arquivo além do console.

`--format-report-file-json <REPORT_FILE>`

Arquivo de relatório de migração de saída como json em vez de mensagens de usuário.

`--skip-backup`

Ignorar movimentação de project.json, global.json, de \*.xproj para um diretório `backup` após a migração bem-sucedida.

## <a name="examples"></a>Exemplos

Migre um projeto no diretório atual e todas as dependências projeto a projeto:

`dotnet migrate`

Migrar todos os projetos para os quais o arquivo *global.json* aponta:

`dotnet migrate path/to/global.json`

Migre apenas o projeto atual e não as dependências projeto a projeto e use uma versão específica do SDK:

`dotnet migrate -s -v 1.0.0-preview4`
