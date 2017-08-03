---
title: "Comando dotnet-msbuild – CLI do .NET Core"
description: "O comando dotnet-msbuild fornece acesso à linha de comando MSBuild."
keywords: dotnet-msmsbuild, CLI, comando da CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 05/24/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: ffdc40ba-ef33-463e-aa35-b0af1fe615a2
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1f02dcd779b9ed249ebd2fedb973383b1dcd8963
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-msbuild"></a>dotnet-msbuild

## <a name="name"></a>Nome

`dotnet-msbuild` – Compila um projeto e todas as suas dependências.

## <a name="synopsis"></a>Sinopse

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>Descrição

O comando `dotnet msbuild` permite o acesso a um MSBuild totalmente funcional.

O comando tem exatamente os mesmos recursos do cliente de linha de comando existente do MSBuild. As opções são todas iguais. Use a [Referência de linha de comando do MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) para obter informações sobre as opções disponíveis. 

## <a name="examples"></a>Exemplos

Compile um projeto e suas dependências:

`dotnet msbuild`

Compile um projeto e suas dependências usando a configuração da Versão:

`dotnet msbuild /p:Configuration=Release`

Execute o destino de publicação e publique para o RID `osx.10.11-x64`:

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`

Confira o projeto inteiro com todos os destinos incluídos pelo SDK:

`dotnet msbuild /pp`

