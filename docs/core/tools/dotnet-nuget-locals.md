---
title: Comando dotnet nuget locals
description: O comando nuget dotnet locals limpa ou lista os recursos locais do NuGet, como cache de solicitação http-, cache temporário ou pasta de pacotes globais em todo o computador.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: cb5747636aa9d04f1ef6a6ff9309ba29c0630dd6
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087400"
---
# <a name="dotnet-nuget-locals"></a>dotnet nuget locals

**Este tópico aplica-se a: ✓** SDK do .NET Core 1.x e versões posteriores

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name

`dotnet nuget locals`-Limpa ou lista os recursos locais do NuGet.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a>Descrição

O comando `dotnet nuget locals` limpa ou lista os recursos locais do NuGet no cache de solicitação http, cache temporário ou pasta de pacotes globais em todo o computador.

## <a name="arguments"></a>Arguments

* **`CACHE_LOCATION`**

  O local do cache a ser listado ou limpo. Aceita um dos seguintes valores:

  * `all` – Indica que a operação especificada aplica-se a todos os tipos cache: o cache de solicitação http, cache de pacotes globais e o cache temporário.
  * `http-cache` – Indica que a operação especificada aplica-se apenas ao cache de solicitação http. Os outros locais do cache não são afetados.
  * `global-packages` – Indica que a operação especificada aplica-se apenas ao cache de pacotes globais. Os outros locais do cache não são afetados.
  * `temp` – Indica que a operação especificada aplica-se apenas ao cache temporário. Os outros locais do cache não são afetados.

## <a name="options"></a>Opções

* **`--force-english-output`**

  Força a execução do aplicativo usando uma cultura invariável com base em inglês.

* **`-h|--help`**

  Imprime uma ajuda breve para o comando.

* **`-c|--clear`**

  A opção clear executa uma operação de limpeza no tipo de cache especificado. O conteúdo dos diretórios de cache é excluído recursivamente. O usuário/grupo executor deve ter permissão nos arquivos nos diretórios de cache. Caso contrário, um erro é exibido, indicando as pastas/os arquivos que não foram limpos.

* **`-l|--list`**

  A opção de lista é usada para exibir a localização do tipo de cache especificado.

## <a name="examples"></a>Exemplos

* Exibe os caminhos de todos os diretórios de cache local (diretório de cache de http, o diretório de cache de pacotes globais e diretório de cache temporário):

  ```dotnetcli
  dotnet nuget locals all –l
  ```

* Exibe o caminho para o diretório local do cache de http:

  ```dotnetcli
  dotnet nuget locals http-cache --list
  ```

* Limpa todos os arquivos dos diretórios de cache local (diretório de cache de http, o diretório de cache de pacotes globais e diretório de cache temporário):

  ```dotnetcli
  dotnet nuget locals all --clear
  ```

* Limpa todos os arquivos no diretório local de cache de pacotes globais:

  ```dotnetcli
  dotnet nuget locals global-packages -c
  ```

* Limpa todos os arquivos no diretório local de cache temporário:

  ```dotnetcli
  dotnet nuget locals temp -c
  ```

## <a name="troubleshooting"></a>Solução de problemas

Para saber mais sobre os problemas e erros mais comuns ao usar o comando `dotnet nuget locals`, veja [Gerenciamento do cache do NuGet](/nuget/consume-packages/managing-the-nuget-cache).
