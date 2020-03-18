---
title: 'Tutorial: Instale e use uma ferramenta global .NET Core'
description: Aprenda a instalar e usar uma ferramenta .NET como ferramenta global.
ms.date: 02/12/2020
ms.openlocfilehash: 9f8378e50fd2544eedbbaaeffb89d67800ec6880
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156732"
---
# <a name="tutorial-install-and-use-a-net-core-global-tool-using-the-net-core-cli"></a>Tutorial: Instale e use uma ferramenta global .NET Core usando o .NET Core CLI

**Este artigo se aplica a:** ✔️ .NET Core 2.1 SDK e versões posteriores

Este tutorial ensina como instalar e usar uma ferramenta global. Você usa uma ferramenta que você cria no [primeiro tutorial desta série](global-tools-how-to-create.md).

## <a name="prerequisites"></a>Pré-requisitos

* Complete o [primeiro tutorial desta série.](global-tools-how-to-create.md)

## <a name="use-the-tool-as-a-global-tool"></a>Use a ferramenta como uma ferramenta global

1. Instale a ferramenta do pacote executando o comando de instalação da [ferramenta dotnet](dotnet-tool-install.md) na pasta de projeto *microsoft.botsay:*

   ```dotnetcli
   dotnet tool install --global --add-source ./nupkg microsoft.botsay
   ```

   O `--global` parâmetro informa ao .NET Core CLI para instalar os binários da ferramenta em um local padrão que é adicionado automaticamente à variável de ambiente PATH.

   O `--add-source` parâmetro informa ao .NET Core CLI que use temporariamente o diretório *./nupkg* como um feed de origem adicional para pacotes NuGet. Você deu ao seu pacote um nome exclusivo para ter certeza de que ele só será encontrado no diretório *./nupkg,* não no site Nuget.org.

   A saída mostra o comando usado para chamar a ferramenta e a versão instalada:

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. Invoque a ferramenta:

   ```console
   botsay hello from the bot
   ```

   > [!NOTE]
   > Se este comando falhar, talvez seja necessário abrir um novo terminal para atualizar o PATH.

1. Remova a ferramenta executando o comando [de saque da ferramenta dotnet:](dotnet-tool-uninstall.md)

   ```dotnetcli
   dotnet tool uninstall -g microsoft.botsay
   ```

## <a name="use-the-tool-as-a-global-tool-installed-in-a-custom-location"></a>Use a ferramenta como uma ferramenta global instalada em um local personalizado

1. Instale a ferramenta a partir do pacote.

   No Windows:

   ```dotnetcli
   dotnet tool install --tool-path c:\dotnet-tools --add-source ./nupkg microsoft.botsay
   ```

   No Linux ou macOS:

   ```dotnetcli
   dotnet tool install --tool-path ~/bin --add-source ./nupkg microsoft.botsay
   ```

   O `--tool-path` parâmetro informa ao .NET Core CLI para instalar os binários da ferramenta no local especificado. Se o diretório não existe, ele é criado. Este diretório não é adicionado automaticamente à variável de ambiente PATH.

   A saída mostra o comando usado para chamar a ferramenta e a versão instalada:

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. Invoque a ferramenta:

   No Windows:

   ```console
   c:\dotnet-tools\botsay hello from the bot
   ```

   No Linux ou macOS:

   ```console
   ~/bin/botsay hello from the bot
   ```

1. Remova a ferramenta executando o comando [de saque da ferramenta dotnet:](dotnet-tool-uninstall.md)

   No Windows:

   ```dotnetcli
   dotnet tool uninstall --tool-path c:\dotnet-tools microsoft.botsay
   ```

   No Linux ou macOS:

   ```dotnetcli
   dotnet tool uninstall --tool-path ~/bin microsoft.botsay
   ```

## <a name="troubleshoot"></a>Solucionar problemas

Se você receber uma mensagem de erro ao seguir o tutorial, consulte [Problemas de uso da ferramenta .NET Core](troubleshoot-usage-issues.md).

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você instalou e usou uma ferramenta como ferramenta global. Para instalar e usar a mesma ferramenta de uma ferramenta local, avance para o próximo tutorial.

> [!div class="nextstepaction"]
> [Instale e use ferramentas locais](local-tools-how-to-use.md)
