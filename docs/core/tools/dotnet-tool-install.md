---
title: Comando dotnet tool install
description: O comando dotnet tool install instala a ferramenta .NET Core especificada na máquina.
ms.date: 02/14/2020
ms.openlocfilehash: 723d25caa6009288dbb55d55f173b04d7b983450
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463358"
---
# <a name="dotnet-tool-install"></a>dotnet tool install

**Este artigo se aplica a:** ✔️ .NET Core 2.1 SDK e versões posteriores

## <a name="name"></a>Nome

`dotnet tool install`- Instala a [ferramenta .NET Core](global-tools.md) especificada na sua máquina.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet tool install <PACKAGE_NAME> -g|--global
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME> --tool-path <PATH>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install -h|--help
```

## <a name="description"></a>Descrição

O `dotnet tool install` comando fornece uma maneira de você instalar ferramentas .NET Core em sua máquina. Para usar o comando, você especifica uma das seguintes opções de instalação:

* Para instalar uma ferramenta global no `--global` local padrão, use a opção.
* Para instalar uma ferramenta global em `--tool-path` um local personalizado, use a opção.
* Para instalar uma ferramenta local, `--global` `--tool-path` omita as opções e opções.

**As ferramentas locais estão disponíveis a partir do .NET Core SDK 3.0.**

As ferramentas globais são instaladas nos seguintes `-g` `--global` diretórios por padrão quando você especifica a opção ou opção:

| Sistema operacional          | Caminho                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

As ferramentas locais são adicionadas a um arquivo *tool-manifest.json* em um diretório *.config* sob o diretório atual. Se um arquivo manifesto ainda não existir, crie-o executando o seguinte comando:

```dotnetcli
dotnet new tool-manifest
```

Para obter mais informações, consulte [Instalar uma ferramenta local](global-tools.md#install-a-local-tool).

## <a name="arguments"></a>Argumentos

- **`PACKAGE_NAME`**

  Nome/ID do pacote NuGet que contém a ferramenta .NET Core a ser instalado.

## <a name="options"></a>Opções

- **`add-source <SOURCE>`**

  Adiciona outra origem do pacote NuGet a ser usada durante a instalação.

- **`configfile <FILE>`**

  O arquivo de configuração do NuGet (*nuget.config*) a ser usado.

- **`framework <FRAMEWORK>`**

  Especifica a [estrutura de destino](../../standard/frameworks.md) para a qual instalar a ferramenta. Por padrão, o SDK do .NET Core tenta escolher a estrutura de destino mais apropriada.

- **`-g|--global`**

  Especifica que a instalação é de todos os usuários. Não pode ser combinada com a opção `--tool-path`. Omitir ambos `--global` e `--tool-path` especificar uma instalação de ferramenta local.

- **`-h|--help`**

  Imprime uma ajuda breve para o comando.

- **`tool-path <PATH>`**

  Especifica o local do qual a Ferramenta Global será instalada. PATH pode ser absoluto ou relativo. Se PATH não existir, o comando tentará criá-lo. Omitir ambos `--global` e `--tool-path` especificar uma instalação de ferramenta local.

- **`-v|--verbosity <LEVEL>`**

  Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.

- **`--version <VERSION_NUMBER>`**

  A versão da ferramenta a ser instalada. Por padrão, a última versão estável do pacote é instalada. Use essa opção para instalar a versão prévia ou versões mais antigas da ferramenta.

## <a name="examples"></a>Exemplos

- **`dotnet tool install -g dotnetsay`**

  Instala [dotnetsay](https://www.nuget.org/packages/dotnetsay/) como uma ferramenta global no local padrão.

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  Instala [dotnetsay](https://www.nuget.org/packages/dotnetsay/) como uma ferramenta global em um diretório específico do Windows.

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  Instala [dotnetsay](https://www.nuget.org/packages/dotnetsay/) como uma ferramenta global em um diretório específico do Linux/macOS.

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  Instala a versão 2.0.0 do [dotnetsay](https://www.nuget.org/packages/dotnetsay/) como uma ferramenta global.

- **`dotnet tool install dotnetsay`**

  Instala [dotnetsay](https://www.nuget.org/packages/dotnetsay/) como uma ferramenta local para o diretório atual.

## <a name="see-also"></a>Confira também

- [.NET Core ferramentas](global-tools.md)
- [Tutorial: Instale e use uma ferramenta global .NET Core usando o .NET Core CLI](global-tools-how-to-use.md)
- [Tutorial: Instale e use uma ferramenta local .NET Core usando o .NET Core CLI](local-tools-how-to-use.md)
