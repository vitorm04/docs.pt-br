---
title: Comando dotnet msbuild
description: O comando dotnet msbuild fornece acesso à linha de comando MSBuild.
ms.date: 02/14/2020
ms.openlocfilehash: 28a32a460d644d3e22f16b5dd9416222ae466e2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503671"
---
# <a name="dotnet-msbuild"></a>dotnet msbuild

**Este artigo se aplica a:** ✔️ .NET Core 2.x SDK e versões posteriores

## <a name="name"></a>Nome

`dotnet msbuild` – Compila um projeto e todas as suas dependências.

## <a name="synopsis"></a>Sinopse

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>Descrição

O comando `dotnet msbuild` permite o acesso a um MSBuild totalmente funcional.

O comando tem exatamente os mesmos recursos que o cliente de linha de comando MSBuild existente apenas para projetos no estilo SDK. As opções são todas iguais. Para obter mais informações sobre as opções disponíveis, consulte a [referência de linha de comando MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).

O comando [dotnet build](dotnet-build.md) é equivalente ao comando `dotnet msbuild -restore -target:Build`. [a compilação dotnet](dotnet-build.md) é mais comumente usada para projetos de construção, `dotnet msbuild` mas como ela sempre executa o alvo de construção, você pode usar quando não quiser construir o projeto. Por exemplo, se você tiver um alvo específico, você `dotnet msbuild` deseja executar sem construir o projeto, use e especifique o destino.

## <a name="examples"></a>Exemplos

- Compile um projeto e suas dependências:

  ```dotnetcli
  dotnet msbuild
  ```

- Compile um projeto e suas dependências usando a configuração da Versão:

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

- Execute o destino de publicação e publique para o RID `osx.10.11-x64`:

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

- Confira o projeto inteiro com todos os destinos incluídos pelo SDK:

  ```dotnetcli
  dotnet msbuild -preprocess
  ```
