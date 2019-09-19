---
title: Comando dotnet msbuild
description: O comando dotnet msbuild fornece acesso à linha de comando MSBuild.
ms.date: 12/03/2018
ms.openlocfilehash: b83f1272cdd4c5fcdb6b1e34aef7692e9acc01cd
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117706"
---
# <a name="dotnet-msbuild"></a>dotnet msbuild

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nome

`dotnet msbuild` – Compila um projeto e todas as suas dependências.

## <a name="synopsis"></a>Sinopse

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>Descrição

O comando `dotnet msbuild` permite o acesso a um MSBuild totalmente funcional.

O comando tem exatamente os mesmos recursos do cliente de linha de comando existente do MSBuild somente para projetos no estilo SDK. As opções são todas iguais. Para obter mais informações sobre as opções disponíveis, confira a [Referência de linha de comando do MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).

O comando [dotnet build](dotnet-build.md) é equivalente ao comando `dotnet msbuild -restore -target:Build`. `dotnet build` é mais comumente usado na criação de projetos, mas `dotnet msbuild` oferece mais controle. Por exemplo, se houver um destino específico que você deseja executar (sem executar o destino do build), convém usar `dotnet msbuild`.

## <a name="examples"></a>Exemplos

* Compile um projeto e suas dependências:

  ```dotnetcli
  dotnet msbuild
  ```

* Compile um projeto e suas dependências usando a configuração da Versão:

  ```dotnetcli
  dotnet msbuild -p:Configuration=Release
  ```

* Execute o destino de publicação e publique para o RID `osx.10.11-x64`:

  ```dotnetcli
  dotnet msbuild -t:Publish -p:RuntimeIdentifiers=osx.10.11-x64
  ```

* Confira o projeto inteiro com todos os destinos incluídos pelo SDK:

  ```dotnetcli
  dotnet msbuild -pp
  ```
