---
title: Comando dotnet-migrate | SDK do .NET Core
description: "O comando dotnet-migrate migra um projeto e todas as suas dependências."
keywords: dotnet-migrate, CLI, comando da CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 11/13/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 70285a83-4103-4617-be8b-d0e1e9a4a91d
translationtype: Human Translation
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: 150d70e3f0a80f7f6e733abee3691a0fe420919f

---

#<a name="dotnet-migrate"></a>dotnet-migrate

## <a name="name"></a>Nome 
dotnet-migrate – migra um projeto da Visualização 2 do .NET Core para um projeto da Visualização 3 do .NET Core

## <a name="synopsis"></a>Sinopse

`dotnet migrate [--help] [--template-file]  
    [--sdk-package-version] [--xproj-file]  
    [--skip-project-references]  [--report-file] [--format-report-file-json]
    [--skip-backup]
    [<arguments>]`

## <a name="description"></a>Descrição
O comando `dotnet migrate` migrará um projeto válido `project.json` baseado na Visualização 2 para um projeto válido `csproj` da Visualização 3. Por padrão, o comando migrará o projeto raiz e as referências de projeto que o projeto raiz contém. Esse comportamento pode ser desabilitado usando a opção `--skip-project-references` no tempo de execução. 

A migração pode ser feita em:

* Um único projeto, especificando o arquivo `project.json` a ser migrado
* Todos os diretórios especificados no arquivo `global.json`, passando um caminho para o arquivo `global.json`
* Em todos os subdiretórios do diretório especificado, recursivamente 

O comando de migração manterá o arquivo migrado `project.json` dentro de um diretório `backup`, que será criado se ainda não existir. Isso pode ser substituído usando a opção `--skip-backup`. 

Por padrão, a operação de migração produzirá o estado do processo de migração para a saída padrão (STDOUT). Se você usar a opção `--report-file`, essa saída também será salva em um arquivo que você especificar. 

Em relação à Visualização 3, o comando `dotnet migrate` dá suporte somente a arquivos `project.json` válidos da Visualização 2. Isso significa que não é possível usá-lo para migrar DNX antigo ou arquivos `project.json` da Visualização 1 diretamente para o csproj; primeiro, é necessário migrá-los para arquivos project.json da Visualização 2 e, em seguida, para arquivos csproj. No futuro, haverá suporte para projetos da Visualização 1. 

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.  

`-t|--template-file <TEMPLATE_FILE>`

Arquivo csproj de modelo a ser usado para migração. Por padrão, o mesmo modelo removido pelo `dotnet new` será usado. 

`-v|--sdk-package-version <VERSION>`

A versão do pacote do sdk que será referenciado no aplicativo migrado. O padrão é a versão do sdk no novo dotnet.

`-x|--xproj-file <FILE>`

O caminho para o arquivo xproj a ser usado. Necessário quando há mais de um xproj em um diretório do projeto.

`-s|--skip-project-references [Debug|Release]`

Ignorar referências de projeto migradas. Por padrão, referências de projeto são migradas recursivamente.

`-r|--report-file <REPORT_FILE>`

Relatório de migração de saída em um arquivo além do console.

`--format-report-file-json <REPORT_FILE>`

Arquivo de relatório de migração de saída como json em vez de mensagens de usuário.

`--skip-backup`

Ignorar movimentação de project.json, global.json, de \*.xproj para um diretório `backup` após a migração bem-sucedida.

## <a name="examples"></a>Exemplos

Migre um projeto no diretório atual e todas as dependências projeto a projeto:

`dotnet migrate`

Migre todos os projetos que apontados pelo arquivo `global.json`:

`dotnet migrate path/to/global.json`

Migre apenas o projeto atual e não as dependências projeto a projeto e use uma versão específica do SDK:

`dotnet migrate -s -v 1.0.0-preview3`




<!--HONumber=Nov16_HO3-->


