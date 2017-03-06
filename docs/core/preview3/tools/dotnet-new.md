---
title: Comando dotnet-new | Microsoft Docs
description: "O comando dotnet-new cria novos projetos .NET Core no diretório atual."
keywords: dotnet-new, CLI, comando da CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 02/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fcc3ed2e-9265-4d50-b59e-dc2e5c190b34
translationtype: Human Translation
ms.sourcegitcommit: 96fd8ea3e55ea33e0bdd0bf3c50a10d0de6db1a1
ms.openlocfilehash: f0c62647c5817db2057c60a7a95a62f08f7889a5

---
#<a name="dotnet-new-net-core-tools-rc4"></a>dotnet-new (Ferramentas do .NET Core RC4)

> [!WARNING]
> Este tópico se aplica às Ferramentas do .NET Core RC4. Para a versão da Visualização 2 das Ferramentas do .NET Core, consulte o tópico [dotnet-new](../../tools/dotnet-new.md).

## <a name="name"></a>Nome
dotnet-new – cria um novo projeto do .NET Core no diretório atual

## <a name="synopsis"></a>Sinopse
```
dotnet new [template] [-lang|--language] [-n|--name] [-o|--output] [-h|--help]
dotnet new [template] [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

## <a name="description"></a>Descrição
O comando `dotnet new` fornece uma maneira conveniente de inicializar um projeto .NET Core válido código-fonte de exemplo para experimentar o conjunto de ferramentas da CLI (Interface de linha de comando). 

Esse comando é invocado no contexto de um diretório. Quando invocado, o comando irá dar suporte aos recursos e arquivos de acordo com o modelo e as opções transmitidos para o comando. 

Depois disso, o projeto estará pronto para ser compilado e/ou editado com mais detalhes. 

## <a name="arguments"></a>Arguments
template – o modelo para instanciar quando o comando é invocado.

O comando contém uma lista padrão de modelos; use `dotnet new --help`. 

## <a name="options"></a>Opções

`-l|--list`         

Modelos de lista contendo o nome especificado.

`-lang|--language`  

Especifica a linguagem do modelo a criar

`-n|--name`         

O nome da saída que está sendo criada. Se nenhum nome for especificado, o nome do diretório atual será usado.

`-o|--output`       

Local para colocar a saída gerada.

`-all|--show-all`   

Mostra todos os modelos para um tipo específico de projeto.

`-h|--help`

Imprime uma ajuda para o comando.

## <a name="template-options"></a>Opções de modelo
Cada modelo de projeto pode ter opções adicionais disponíveis. Os modelos básicos, por exemplo, têm o seguinte.

**console, xunit, mstest**

`-f|--framework` – especifica a qual estrutura se destina. Valores: netcoreapp1.0 ou netcoreapp1.1 (Padrão: netcoreapp1.0)

**web, webapi**

`-f|--framework` – especifica a qual estrutura se destina. Valores: netcoreapp1.0 ou netcoreapp1.1 (Padrão: netcoreapp1.0)
 
**mvc**

`-f|--framework` – especifica a qual estrutura se destina. Valores: netcoreapp1.0 ou netcoreapp1.1 (Padrão: netcoreapp1.0)

`-au|--authentication` – o tipo de autenticação usado. Valores: Nenhum ou Individual (Padrão: Nenhum)

`-uld|--use-local-db` – Se deve usar ou não o LocalDB em vez do SQLite. Valores: verdadeiro ou falso (Padrão: falso)

**classlib**

`-f|--framework` – especifica a qual estrutura se destina. Valores: netcoreapp1.0, netcoreapp1.1 e netstandard1.0 – 1.6 (Padrão: netstandard1.4).

## <a name="examples"></a>Exemplos

Crie um projeto de aplicativo de console F# no diretório atual:

`dotnet new console -lang f#` 
   
Crie um novo projeto de aplicativo de MVC C# do ASP.NET Core no diretório atual sem autenticação destinado ao .NET Core 1.0:  

`dotnet new mvc -au None -f netcoreapp1.0`
 
Crie um novo aplicativo XUnit destinado ao .NET Core 1.1:

`dotnet new xunit --Framework netcoreapp1.1`

Lista todos os modelos disponíveis para o MVC:

`dotnet new mvc -l`


<!--HONumber=Feb17_HO3-->


