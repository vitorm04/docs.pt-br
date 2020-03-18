---
title: .NET Core ferramentas
description: Como instalar, usar, atualizar e remover ferramentas .NET Core. Abrange ferramentas globais, ferramentas de caminho de ferramentas e ferramentas locais.
author: KathleenDollard
ms.date: 02/12/2020
ms.openlocfilehash: 2f0101c6385c41eda49bcb2458428c1f14552617
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847775"
---
# <a name="how-to-manage-net-core-tools"></a>Como gerenciar ferramentas .NET Core

**Este artigo se aplica a:** ✔️ .NET Core 2.1 SDK e versões posteriores

Uma ferramenta .NET Core é um pacote NuGet especial que contém um aplicativo de console. Uma ferramenta pode ser instalada na sua máquina das seguintes maneiras:

* Como uma ferramenta global.

  Os binários da ferramenta são instalados em um diretório padrão que é adicionado à variável ambiente PATH. Você pode invocar a ferramenta de qualquer diretório na máquina sem especificar sua localização. Uma versão de uma ferramenta é usada para todos os diretórios da máquina.

* Como uma ferramenta global em um local personalizado (também conhecido como ferramenta de caminho de ferramentas).

  Os binários da ferramenta são instalados em um local que você especifica. Você pode invocar a ferramenta a partir do diretório de instalação ou fornecendo o diretório com o nome do comando ou adicionando o diretório à variável ambiente PATH. Uma versão de uma ferramenta é usada para todos os diretórios da máquina.

* Como uma ferramenta local (aplica-se ao .NET Core SDK 3.0 e posterior).

  Os binários da ferramenta são instalados em um diretório padrão. Você invoca a ferramenta do diretório de instalação ou de qualquer um de seus subdiretórios. Diretórios diferentes podem usar versões diferentes da mesma ferramenta.
  
  O .NET CLI usa arquivos manifestos para acompanhar quais ferramentas são instaladas como locais para um diretório. Quando o arquivo manifesto é salvo no diretório raiz de um repositório de código fonte, um colaborador pode clonar o repositório e invocar um único comando .NET Core CLI que instala todas as ferramentas listadas nos arquivos manifestos.

> [!IMPORTANT]
> As ferramentas .NET Core são executadas em total confiança. Não instale uma ferramenta .NET Core a menos que confie no autor.

## <a name="find-a-tool"></a>Encontre uma ferramenta

Atualmente, o .NET Core não possui um recurso de pesquisa de ferramentas. Aqui estão algumas maneiras de encontrar ferramentas:

* Veja a lista de ferramentas no repositório GitHub [de ferramentas natemcmaster/dotnet.](https://github.com/natemcmaster/dotnet-tools)
* Use [toolGet](https://www.toolget.net/) para procurar ferramentas .NET.
* Consulte o código-fonte das ferramentas criadas pela equipe do ASP.NET Core no [diretório Tools do repositório Dotnet/Aspnetcore GitHub](https://github.com/dotnet/aspnetcore/tree/master/src/Tools).
* Saiba mais sobre ferramentas de diagnóstico em [ferramentas de diagnóstico .NET Core .](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools)
* Pesquise no site da [NuGet.](https://www.nuget.org) No entanto, o site NuGet ainda não possui um recurso que permite pesquisar apenas pacotes de ferramentas.

## <a name="check-the-author-and-statistics"></a>Verificar o autor e as estatísticas

Como as ferramentas do .NET Core são executadas em total confiança e as ferramentas globais são adicionadas à variável ambiente PATH, elas podem ser muito poderosas. Não baixe ferramentas de pessoas em quem você não confia.

Se a ferramenta estiver hospedada no NuGet, você pode verificar o autor e as estatísticas pesquisando a ferramenta.

## <a name="install-a-global-tool"></a>Instale uma ferramenta global

Para instalar uma ferramenta como ferramenta `-g` `--global` global, use a ou opção de instalação da [ferramenta dotnet,](dotnet-tool-install.md)como mostrado no exemplo a seguir:

```dotnetcli
dotnet tool install -g dotnetsay
```

A saída mostra o comando usado para invocar a ferramenta e a versão instalada, semelhante ao exemplo a seguir:

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
```

O local padrão para binários de uma ferramenta depende do sistema operacional:

| Sistema operacional          | Caminho                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Esse local é adicionado ao caminho do usuário quando o SDK é executado pela primeira vez, para que as ferramentas globais possam ser invocadas de qualquer diretório sem especificar a localização da ferramenta.

O acesso à ferramenta é específico do usuário, não da máquina global. Uma ferramenta global só está disponível para o usuário que instalou a ferramenta.

### <a name="install-a-global-tool-in-a-custom-location"></a>Instale uma ferramenta global em um local personalizado

Para instalar uma ferramenta como uma ferramenta global `--tool-path` em um local personalizado, use a opção de instalação da [ferramenta dotnet,](dotnet-tool-install.md)como mostrado nos exemplos a seguir.

No Windows:

```dotnetcli
dotnet tool install dotnetsay --tool-path c:\dotnet-tools
```

No Linux ou macOS:

```dotnetcli
dotnet tool install dotnetsay --tool-path ~/bin
```

O .NET Core SDK não adiciona esse local automaticamente à variável ambiente PATH. Para [invocar uma ferramenta de caminho de ferramenta,](#invoke-a-tool-path-tool)você tem que ter certeza de que o comando está disponível usando um dos seguintes métodos:

* Adicione o diretório de instalação à variável ambiente PATH.
* Especifique o caminho completo para a ferramenta quando você invocá-la.
* Invoque a ferramenta de dentro do diretório de instalação.

## <a name="install-a-local-tool"></a>Instale uma ferramenta local

**Aplica-se ao .NET Core 3.0 SDK e posteriormente.**

Para instalar uma ferramenta apenas para acesso local (para o diretório atual e subdiretórios), ele precisa ser adicionado a um arquivo manifesto de ferramenta. Para criar um arquivo manifesto `dotnet new tool-manifest` de ferramenta, execute o comando:

```dotnetcli
dotnet new tool-manifest
```

Este comando cria um arquivo manifesto chamado *dotnet-tools.json* o diretório *.config.* Para adicionar uma ferramenta local ao arquivo manifesto, use o comando `--global` de `--tool-path` instalação da [ferramenta dotnet](dotnet-tool-install.md) e **omita** as opções e opções, como mostrado no exemplo a seguir:

```dotnetcli
dotnet tool install dotnetsay
```

A saída de comando mostra em qual arquivo manifesto a ferramenta recém-instalada está, semelhante ao exemplo a seguir:

```console
You can invoke the tool from this directory using the following command:
dotnet tool run dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
Entry is added to the manifest file /home/name/botsay/.config/dotnet-tools.json.
```

O exemplo a seguir mostra um arquivo manifesto com duas ferramentas locais instaladas:

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "botsay": {
      "version": "1.0.0",
      "commands": [
        "botsay"
      ]
    },
    "dotnetsay": {
      "version": "2.1.3",
      "commands": [
        "dotnetsay"
      ]
    }
  }
}
```

Você normalmente adiciona uma ferramenta local ao diretório raiz do repositório. Depois de verificar o arquivo manifesto no repositório, os desenvolvedores que verificam o código do repositório recebem o arquivo manifesto mais recente. Para instalar todas as ferramentas listadas no `dotnet tool restore` arquivo manifesto, eles executam o comando:

```dotnetcli
dotnet tool restore
```

A saída indica quais ferramentas foram restauradas:

```console
Tool 'botsay' (version '1.0.0') was restored. Available commands: botsay
Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
Restore was successful.
```

## <a name="install-a-specific-tool-version"></a>Instale uma versão específica da ferramenta

Para instalar uma versão de pré-lançamento ou uma versão específica `--version` de uma ferramenta, especifique o número da versão usando a opção, como mostrado no exemplo a seguir:

```dotnetcli
dotnet tool install dotnetsay --version 2.1.3
```

## <a name="use-a-tool"></a>Use uma ferramenta

O comando que você usa para invocar uma ferramenta pode ser diferente do nome do pacote que você instala. Para exibir todas as ferramentas atualmente instaladas na máquina para o usuário atual, use o comando [dotnet tool list:](dotnet-tool-list.md)

```dotnetcli
dotnet tool list
```

A saída mostra a versão e o comando de cada ferramenta, semelhante ao exemplo a seguir:

```console
Package Id      Version      Commands       Manifest
-------------------------------------------------------------------------------------------
botsay          1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
dotnetsay       2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
```

Como mostrado neste exemplo, a lista mostra ferramentas locais. Para ver ferramentas globais, use a `--global` opção e para `--tool-path` ver ferramentas de caminho de ferramentas, use a opção.

### <a name="invoke-a-global-tool"></a>Invoque uma ferramenta global

Para ferramentas globais, use o comando da ferramenta por si só. Por exemplo, se `dotnetsay` o `dotnet-doc`comando é ou , é isso que você usa para invocar o comando:

```console
dotnetsay
dotnet-doc
```

Se o comando começar `dotnet-`com o prefixo, uma maneira `dotnet` alternativa de invocar a ferramenta é usar o comando e omitir o prefixo de comando da ferramenta. Por exemplo, se `dotnet-doc`o comando for, o seguinte comando invoca a ferramenta:

```dotnetcli
dotnet doc
```

No entanto, no seguinte cenário, `dotnet` você não pode usar o comando para invocar uma ferramenta global:

* Uma ferramenta global e uma ferramenta local `dotnet-`têm o mesmo comando prefixado por .
* Você deseja invocar a ferramenta global de um diretório que esteja no escopo da ferramenta local.

Neste cenário, `dotnet doc` `dotnet dotnet-doc` e invoque a ferramenta local. Para invocar a ferramenta global, use o comando por si só:

```dotnetcli
dotnet-doc
```

### <a name="invoke-a-tool-path-tool"></a>Invoque uma ferramenta de caminho de ferramenta

Para invocar uma ferramenta global que `tool-path` seja instalada usando a opção, certifique-se de que o comando esteja disponível, conforme explicado [anteriormente neste artigo](#install-a-global-tool-in-a-custom-location).

### <a name="invoke-a-local-tool"></a>Invoque uma ferramenta local

Para invocar uma ferramenta local, `dotnet` você tem que usar o comando de dentro do diretório de instalação. Você pode usar a`dotnet tool run <COMMAND_NAME>`forma longa (`dotnet <COMMAND_NAME>`) ou a forma curta ( ), como mostrado nos exemplos a seguir:

```dotnetcli
dotnet tool run dotnetsay
dotnet dotnetsay
```

Se o comando for `dotnet-`prefixado por , você pode incluir ou omiti-lo o prefixo quando você invocar a ferramenta. Por exemplo, se `dotnet-doc`o comando for, qualquer um dos seguintes exemplos invoca a ferramenta local:

```dotnetcli
dotnet tool run dotnet-doc
dotnet dotnet-doc
dotnet doc
```

## <a name="update-a-tool"></a>Atualize uma ferramenta

Atualizar uma ferramenta envolve desinstalar e reinstalá-la com a versão estável mais recente. Para atualizar uma ferramenta, use o comando [dotnet tool update](dotnet-tool-update.md) com a mesma opção que você usou para instalar a ferramenta:

```dotnetcli
dotnet tool update --global <packagename>
dotnet tool update --tool-path <packagename>
dotnet tool update <packagename>
```

Para uma ferramenta local, o SDK encontra o primeiro arquivo manifesto que contém o ID do pacote olhando no diretório atual e nos diretórios-pai. Se não houver tal ID de pacote em qualquer arquivo manifesto, o SDK adiciona uma nova entrada ao arquivo manifesto mais próximo.

## <a name="uninstall-a-tool"></a>Desinstale uma ferramenta

Remova uma ferramenta usando o comando [de saque da ferramenta dotnet](dotnet-tool-uninstall.md) com a mesma opção que você usou para instalar a ferramenta:

```dotnetcli
dotnet tool uninstall --global <packagename>
dotnet tool uninstall --tool-path<packagename>
dotnet tool uninstall <packagename>
```

Para uma ferramenta local, o SDK encontra o primeiro arquivo manifesto que contém o ID do pacote olhando no diretório atual e nos diretórios-pai.

## <a name="get-help-and-troubleshoot"></a>Obter ajuda e solucionar problemas

Para obter uma `dotnet tool` lista de comandos disponíveis, digite o seguinte comando:

```dotnetcli
dotnet tool --help
```

Para obter instruções de uso da ferramenta, digite um dos seguintes comandos ou consulte o site da ferramenta:

```dotnetcli
<command> --help
dotnet <command> --help
```

Se uma ferramenta não for instalada ou executada, consulte [Problemas de uso da ferramenta .NET Core](troubleshoot-usage-issues.md).

## <a name="see-also"></a>Confira também

- [Tutorial: Crie uma ferramenta .NET Core usando o .NET Core CLI](global-tools-how-to-create.md)
- [Tutorial: Instale e use uma ferramenta global .NET Core usando o .NET Core CLI](global-tools-how-to-use.md)
- [Tutorial: Instale e use uma ferramenta local .NET Core usando o .NET Core CLI](local-tools-how-to-use.md)
