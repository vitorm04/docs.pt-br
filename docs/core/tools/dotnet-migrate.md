---
title: "Comando dotnet-migrate – CLI do .NET Core"
description: "O comando dotnet-migrate migra um projeto e todas as suas dependências."
keywords: dotnet-migrate, CLI, comando da CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 0da07253-5ae1-42e9-9455-bffee9950952
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e8491d69b2e0df7b3bd2741e34abdb9631777019
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-migrate"></a>dotnet-migrate

## <a name="name"></a>Nome

`dotnet-migrate` - Migrar um projeto do .NET Core Visualização 2 para um projeto do SDK 1.0 do .NET Core.

## <a name="synopsis"></a>Sinopse

`dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file] [-s|--skip-project-references] [-r|--report-file] [--format-report-file-json] [--skip-backup] [-h|--help]`

## <a name="description"></a>Descrição

O comando `dotnet migrate` migra um projeto válido baseado em *project.json* da Visualização 2 para um projeto *csproj* válido do SDK 1.0 do .NET Core. 

Por padrão, o comando migra o projeto raiz e as referências de projeto que o projeto raiz contém. Esse comportamento é desabilitado usando a opção `--skip-project-references` no tempo de execução. 

A migração é executada no seguinte:

* Um único projeto, especificando o arquivo *project.json* a ser migrado.
* Todos os diretórios especificados no arquivo *global.json*, passando um caminho para o arquivo *global.json*.
* O arquivo *solution.sln*, onde ele migra os projetos referenciados na solução.
* Em todos os subdiretórios do diretório especificado, recursivamente.

O comando `dotnet migrate` mantém o arquivo *project.json* migrado em um diretório `backup`, que será criado se ainda não existir. Esse comportamento pode ser substituído usando a opção `--skip-backup`. 

Por padrão, a operação de migração produzirá o estado do processo de migração para a saída padrão (STDOUT). Se você usar a opção `--report-file <REPORT_FILE>`, a saída será salva no arquivo especificado. 

O comando `dotnet migrate` dá suporte apenas a projetos com base em *project.json* da Visualização 2. Isso significa que você não pode usá-lo para migrar projetos com base em *project.json* de DNX ou Visualização 1 diretamente para projetos de MSBuild/csproj. Primeiro, você precisa migrar manualmente o projeto para um projeto com base em *project.json* de Visualização 2 e, em seguida, usar o comando `dotnet migrate` para migrar o projeto.

## <a name="arguments"></a>Arguments

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

O caminho até um dos seguintes:

* um arquivo *project.json* a ser migrado.
* um arquivo *global.json*, ele migrará as pastas especificadas em *global.json*.
* um arquivo *solution.sln*, ele migrará os projetos referenciados na solução.
* um diretório para migração, ele procurará recursivamente por arquivos *project.json* para migrar.

Se nada for especificado, o padrão será o diretório atual.

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.  

`-t|--template-file <TEMPLATE_FILE>`

Arquivo csproj de modelo a ser usado para migração. Por padrão, o mesmo modelo removido por `dotnet new console` será usado. 

`-v|--sdk-package-version <VERSION>`

A versão do pacote do sdk referenciada no aplicativo migrado. O padrão é a versão do SDK no `dotnet new`.

`-x|--xproj-file <FILE>`

O caminho para o arquivo xproj a ser usado. Necessário quando há mais de um xproj em um diretório do projeto.

`-s|--skip-project-references [Debug|Release]`

Ignorar referências de projeto migradas. Por padrão, as referências de projeto são migradas recursivamente.

`-r|--report-file <REPORT_FILE>`

Relatório de migração de saída em um arquivo além do console.

`--format-report-file-json <REPORT_FILE>`

Arquivo de relatório de migração de saída como JSON em vez de mensagens de usuário.

`--skip-backup`

Ignorar a movimentação de *project.json*, *global.json* e *\*.xproj* para um diretório `backup` após a migração bem-sucedida.

## <a name="examples"></a>Exemplos

Migre um projeto no diretório atual e todas as dependências projeto a projeto:

`dotnet migrate`

Migre todos os projetos incluídos pelo arquivo *global.json*:

`dotnet migrate path/to/global.json`

Migre apenas o projeto atual e não as dependências P2P (projeto a projeto). Além disso, use uma versão específica do SDK:

`dotnet migrate -s -v 1.0.0-preview4`

