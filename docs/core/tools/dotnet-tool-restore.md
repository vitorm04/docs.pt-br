---
title: comando de restauração de ferramenta dotnet
description: O comando dotnet tool restore instala em sua máquina as ferramentas locais .NET Core que estão no escopo do diretório atual.
ms.date: 02/14/2020
ms.openlocfilehash: 0d1e67ec809ddd725721698cc741f9acc99e1ce7
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389609"
---
# <a name="dotnet-tool-restore"></a>dotnet tool restore

**Este artigo se aplica a:** ✔️ .NET Core 3.0 SDK e versões posteriores

## <a name="name"></a>Nome

`dotnet tool restore`- Instala na sua máquina as ferramentas locais .NET Core que estão no escopo do diretório atual.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet tool restore <PACKAGE_NAME>
    [--configfile] [--add-source] [tool-manifest]
    [--disable-parallel] [--ignore-failed-sources]
    [--no-cache] [--interactive] [-v|--verbosity]

dotnet tool restore <-h|--help>
```

## <a name="description"></a>Descrição

O `dotnet tool restore` comando encontra o arquivo manifesto da ferramenta que está no escopo do diretório atual e instala as ferramentas listadas nele. Para obter informações sobre arquivos manifestos, consulte [Instalar uma ferramenta local](global-tools.md#install-a-local-tool) e Invocar uma ferramenta [local](global-tools.md#invoke-a-local-tool).

## <a name="arguments"></a>Argumentos

- **`PACKAGE_NAME`**

Nome/ID do pacote NuGet que contém a ferramenta .NET Core a ser instalado.

## <a name="options"></a>Opções

- **`--configfile <FILE>`**

  O arquivo de configuração do NuGet (*nuget.config*) a ser usado.

- **`--add-source <SOURCE>`**

  Adiciona outra origem do pacote NuGet a ser usada durante a instalação.

- **`--tool-manifest <PATH>`**

  Caminho para o arquivo manifesto.

- **`--disable-parallel`**

  Evite restaurar vários projetos em paralelo.

- **`--ignore-failed-sources`**

  Trate as falhas da fonte do pacote como avisos.

- **`--no-cache`**

  Não faça cache de pacotes e solicitações http.

- **`--interactive`**

  Permite que o comando pare e aguarde a entrada ou uma ação do usuário (por exemplo, para concluir a autenticação).

- **`-h|--help`**

  Imprime uma ajuda breve para o comando.

- **`-v|--verbosity <LEVEL>`**

  Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.

## <a name="example"></a>Exemplo

- **`dotnet tool restore`**

  Restaura ferramentas locais para o diretório atual.

## <a name="see-also"></a>Confira também

- [.NET Core ferramentas](global-tools.md)
- [Tutorial: Instale e use uma ferramenta local .NET Core usando o .NET Core CLI](local-tools-how-to-use.md)
