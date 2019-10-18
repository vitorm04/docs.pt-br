---
title: Comando dotnet-add reference
description: O comando dotnet add reference fornece uma opção conveniente para adicionar referências projeto a projeto.
ms.date: 06/26/2019
ms.openlocfilehash: 79c8a787079e02f6cf227820c24bb4157b0292c6
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522774"
---
# <a name="dotnet-add-reference"></a>Referência dotnet-add

**Este artigo se aplica a: ✓** SDK do .NET Core 1.x e versões posteriores

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name

`dotnet add reference` – Adiciona as referências P2P (projeto a projeto).

## <a name="synopsis"></a>Sinopse

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help] [--interactive]`

## <a name="description"></a>Descrição

O comando `dotnet add reference` fornece uma opção conveniente para adicionar referências de projeto a um projeto. Depois de executar o comando, os elementos de `<ProjectReference>` são adicionados ao arquivo de projeto.

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a>Arguments

- **`PROJECT`**

  Especifica o arquivo do projeto. Se não for especificado, o comando pesquisará um no diretório atual.

- **`PROJECT_REFERENCES`**

  Referências P2P (projeto a projeto) a serem adicionadas. Especifique um ou mais projetos. Os [padrões Glob](https://en.wikipedia.org/wiki/Glob_(programming)) são compatíveis com sistemas baseados em Unix/Linux.

## <a name="options"></a>Opções

- **`-h|--help`**

  Imprime uma ajuda breve para o comando.

- **`-f|--framework <FRAMEWORK>`**

  Adiciona referências de projeto somente quando há uma [estrutura](../../standard/frameworks.md) específica como destino.

- **`--interactive`**

  Permite que o comando pare e aguarde a entrada ou uma ação do usuário (por exemplo, para concluir a autenticação). Disponível desde o SDK do .NET Core 3.0.

## <a name="examples"></a>Exemplos

- Adicionar referência de projeto:

  ```dotnetcli
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

- Adicionar várias referências de projeto ao projeto no diretório atual:

  ```dotnetcli
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- Adicionar várias referências de projeto usando um padrão de recurso de curinga no Linux/Unix:

  ```dotnetcli
  dotnet add app/app.csproj reference **/*.csproj
  ```
