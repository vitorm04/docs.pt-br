---
title: Comando dotnet nuget locals
description: O comando nuget dotnet locals limpa ou lista os recursos locais do NuGet, como cache de solicitação http-, cache temporário ou pasta de pacotes globais em todo o computador.
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: 3fdd7d946b08b4c18cfaeb65013de259b927a7fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503689"
---
# <a name="dotnet-nuget-locals"></a>dotnet nuget locals

**Este artigo se aplica a:** ✔️ .NET Core 2.x SDK e versões posteriores

## <a name="name"></a>Nome

`dotnet nuget locals`-Limpa ou lista os recursos locais do NuGet.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a>Descrição

O comando `dotnet nuget locals` limpa ou lista os recursos locais do NuGet no cache de solicitação http, cache temporário ou pasta de pacotes globais em todo o computador.

## <a name="arguments"></a>Argumentos

- **`CACHE_LOCATION`**

  O local do cache a ser listado ou limpo. Aceita um dos seguintes valores:

  * `all` – Indica que a operação especificada aplica-se a todos os tipos cache: o cache de solicitação http, cache de pacotes globais e o cache temporário.
  * `http-cache` – Indica que a operação especificada aplica-se apenas ao cache de solicitação http. Os outros locais do cache não são afetados.
  * `global-packages` – Indica que a operação especificada aplica-se apenas ao cache de pacotes globais. Os outros locais do cache não são afetados.
  * `temp` – Indica que a operação especificada aplica-se apenas ao cache temporário. Os outros locais do cache não são afetados.

## <a name="options"></a>Opções

- **`--force-english-output`**

  Força a execução do aplicativo usando uma cultura invariável com base em inglês.

- **`-h|--help`**

  Imprime uma ajuda breve para o comando.

- **`-c|--clear`**

  A opção clear executa uma operação de limpeza no tipo de cache especificado. O conteúdo dos diretórios de cache é excluído recursivamente. O usuário/grupo executor deve ter permissão nos arquivos nos diretórios de cache. Caso contrário, um erro é exibido, indicando as pastas/os arquivos que não foram limpos.

- **`-l|--list`**

  A opção de lista é usada para exibir a localização do tipo de cache especificado.

## <a name="examples"></a>Exemplos

- Exibe os caminhos de todos os diretórios de cache local (diretório de cache de http, o diretório de cache de pacotes globais e diretório de cache temporário):

  ```dotnetcli
  dotnet nuget locals all –l
  ```

- Exibe o caminho para o diretório local do cache de http:

  ```dotnetcli
  dotnet nuget locals http-cache --list
  ```

- Limpa todos os arquivos dos diretórios de cache local (diretório de cache de http, o diretório de cache de pacotes globais e diretório de cache temporário):

  ```dotnetcli
  dotnet nuget locals all --clear
  ```

- Limpa todos os arquivos no diretório local de cache de pacotes globais:

  ```dotnetcli
  dotnet nuget locals global-packages -c
  ```

- Limpa todos os arquivos no diretório local de cache temporário:

  ```dotnetcli
  dotnet nuget locals temp -c
  ```

## <a name="troubleshooting"></a>Solução de problemas

Para saber mais sobre os problemas e erros mais comuns ao usar o comando `dotnet nuget locals`, veja [Gerenciamento do cache do NuGet](/nuget/consume-packages/managing-the-nuget-cache).
