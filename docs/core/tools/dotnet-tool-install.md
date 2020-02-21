---
title: Comando dotnet tool install
description: O comando dotnet ferramenta de instalação instala a ferramenta .NET Core especificada em seu computador.
ms.date: 02/14/2020
ms.openlocfilehash: 2705defe9b77009ca1411da28dd86d144ccc19e6
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543463"
---
# <a name="dotnet-tool-install"></a>dotnet tool install

**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores

## <a name="name"></a>Nome

`dotnet tool install`-instala a [ferramenta .NET Core](global-tools.md) especificada em seu computador.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet tool install <PACKAGE_NAME> <-g|--global> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> <--tool-path> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <-h|--help>
```

## <a name="description"></a>DESCRIÇÃO

O comando `dotnet tool install` fornece uma maneira de instalar as ferramentas do .NET Core em seu computador. Para usar o comando, especifique uma das seguintes opções de instalação:

* Para instalar uma ferramenta global no local padrão, use a opção `--tool-path`.
* Para instalar uma ferramenta global em um local personalizado, use a opção `--tool-path`.
* Para instalar uma ferramenta local, omita as opções `--global` e `--tool-path`.

**As ferramentas locais estão disponíveis a partir do SDK do .NET Core 3,0.**

As ferramentas globais são instaladas nos diretórios a seguir por padrão, quando você especifica a opção `-g` ou `--global`:

| Sistema operacional          | Caminho                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

As ferramentas locais são adicionadas a um arquivo de *ferramenta-manifest. JSON* em um diretório *. config* no diretório atual. Se um arquivo de manifesto ainda não existir, crie-o executando o seguinte comando:

```dotnetcli
dotnet new tool-manifest
```

Para obter mais informações, consulte [instalar uma ferramenta local](global-tools.md#install-a-local-tool).

## <a name="arguments"></a>Argumentos

- **`PACKAGE_NAME`**

  Nome/ID do pacote NuGet que contém a ferramenta .NET Core a ser instalada.

## <a name="options"></a>Opções

- **`add-source <SOURCE>`**

  Adiciona outra origem do pacote NuGet a ser usada durante a instalação.

- **`configfile <FILE>`**

  O arquivo de configuração do NuGet (*nuget.config*) a ser usado.

- **`framework <FRAMEWORK>`**

  Especifica a [estrutura de destino](../../standard/frameworks.md) para a qual instalar a ferramenta. Por padrão, o SDK do .NET Core tenta escolher a estrutura de destino mais apropriada.

- **`-g|--global`**

  Especifica que a instalação é de todos os usuários. Não pode ser combinada com a opção `--tool-path`. Omitir `--global` e `--tool-path` especifica uma instalação de ferramenta local. 

- **`-h|--help`**

  Imprime uma ajuda breve para o comando.

- **`tool-path <PATH>`**

  Especifica o local do qual a Ferramenta Global será instalada. PATH pode ser absoluto ou relativo. Se PATH não existir, o comando tentará criá-lo. Omitir `--global` e `--tool-path` especifica uma instalação de ferramenta local. 

- **`-v|--verbosity <LEVEL>`**

  Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.

- **`--version <VERSION_NUMBER>`**

  A versão da ferramenta a ser instalada. Por padrão, a última versão estável do pacote é instalada. Use essa opção para instalar a versão prévia ou versões mais antigas da ferramenta.

## <a name="examples"></a>Exemplos

- **`dotnet tool install -g dotnetsay`**

  Instala o [dotnetsay](https://www.nuget.org/packages/dotnetsay/) como uma ferramenta global no local padrão.

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  Instala o [dotnetsay](https://www.nuget.org/packages/dotnetsay/) como uma ferramenta global em um diretório específico do Windows.

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  Instala o [dotnetsay](https://www.nuget.org/packages/dotnetsay/) como uma ferramenta global em um diretório específico do linux/MacOS.

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  Instala a versão 2.0.0 do [dotnetsay](https://www.nuget.org/packages/dotnetsay/) como uma ferramenta global.

- **`dotnet tool install dotnetsay`**

  Instala o [dotnetsay](https://www.nuget.org/packages/dotnetsay/) como uma ferramenta local para o diretório atual.

## <a name="see-also"></a>Confira também

- [Ferramentas do .NET Core](global-tools.md)
