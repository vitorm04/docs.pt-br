---
title: Comando dotnet-msbuild - CLI do .NET Core | Microsoft Docs
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
ms.translationtype: Human Translation
ms.sourcegitcommit: df4b2ddd322e4bd2ebaf444439107e88a983f988
ms.openlocfilehash: 2267ef0b5785959456ea443405b6708a423d00ba
ms.contentlocale: pt-br
ms.lasthandoff: 05/30/2017

---

<a id="dotnet-msbuild" class="xliff"></a>

# dotnet-msbuild

<a id="name" class="xliff"></a>

## Nome

`dotnet-msbuild` – Compila um projeto e todas as suas dependências.

<a id="synopsis" class="xliff"></a>

## Sinopse

`dotnet msbuild <msbuild_arguments> [-h]`

<a id="description" class="xliff"></a>

## Descrição

O comando `dotnet msbuild` permite o acesso a um MSBuild totalmente funcional.

O comando tem exatamente os mesmos recursos do cliente de linha de comando existente do MSBuild. As opções são todas iguais. Use a [Referência de linha de comando do MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-command-line-reference) para obter informações sobre as opções disponíveis. 

<a id="examples" class="xliff"></a>

## Exemplos

Compile um projeto e suas dependências:

`dotnet msbuild`

Compile um projeto e suas dependências usando a configuração da Versão:

`dotnet msbuild /p:Configuration=Release`

Execute o destino de publicação e publique para o RID `osx.10.11-x64`:

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`

Confira o projeto inteiro com todos os destinos incluídos pelo SDK:

`dotnet msbuild /pp`
