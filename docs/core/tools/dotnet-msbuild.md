---
title: Comando dotnet msbuild – CLI do .NET Core
description: O comando dotnet msbuild fornece acesso à linha de comando MSBuild.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 76165590478b0e76d19d546c87e012da4716b6db
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/29/2018
ms.locfileid: "47421184"
---
# <a name="dotnet-msbuild"></a>dotnet msbuild

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nome

`dotnet msbuild` – Compila um projeto e todas as suas dependências.

## <a name="synopsis"></a>Sinopse

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>Descrição

O comando `dotnet msbuild` permite o acesso a um MSBuild totalmente funcional.

O comando tem exatamente os mesmos recursos do cliente de linha de comando existente do MSBuild. As opções são todas iguais. Para obter mais informações sobre as opções disponíveis, confira a [Referência de linha de comando do MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).

## <a name="examples"></a>Exemplos

Compile um projeto e suas dependências:

`dotnet msbuild`

Compile um projeto e suas dependências usando a configuração da Versão:

`dotnet msbuild -p:Configuration=Release`

Execute o destino de publicação e publique para o RID `osx.10.11-x64`:

`dotnet msbuild -t:Publish -p:RuntimeIdentifiers=osx.10.11-x64`

Confira o projeto inteiro com todos os destinos incluídos pelo SDK:

`dotnet msbuild -pp`
