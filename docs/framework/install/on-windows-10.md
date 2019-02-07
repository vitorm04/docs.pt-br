---
title: Instalar o .NET Framework no Windows 10
description: Saiba como instalar o .NET Framework no Windows 10 ou no Windows Server 2016.
author: rlander
ms.author: mairaw
ms.date: 04/10/2018
ms.custom: updateeachrelease
ms.openlocfilehash: db5c6a45db299d716b2fdd115086e0dbc5952a59
ms.sourcegitcommit: e39d93d358974b9ed4541cedf4e25c0101015c3c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2019
ms.locfileid: "55204295"
---
# <a name="install-the-net-framework-on-windows-10-and-windows-server-2016-and-later"></a>Instalar o .NET Framework no Windows 10 e no Windows Server 2016 e posterior

O .NET Framework é necessário para executar muitos aplicativos no Windows. As instruções neste artigo devem ajudá-lo a instalar as versões do .NET Framework que você precisa. O [.NET Framework 4.7.2](https://dotnet.microsoft.com/download/dotnet-framework-runtime/net472) é a última versão disponível.

Você pode ter chegado nesta página depois de tentar executar um aplicativo e ver uma caixa de diálogo em seu computador semelhante à seguinte:

![Não foi possível iniciar o aplicativo](./media/this-application-could-not-be-started.png)

## <a name="net-framework-472"></a>.NET Framework 4.7.2

O .NET Framework 4.7.2 está incluído na:

* [Atualização de outubro de 2018 para o Windows 10](https://support.microsoft.com/help/4028685/windows-10-get-the-update)

* [Atualização de abril de 2018 do Windows 10](https://www.microsoft.com/software-download/windows10)

* Windows Server 2019

* Windows Server, versão 1809

* Windows Server, versão 1803

> [!div class="button"]
> [Baixe o .NET Framework 4.7.2](https://dotnet.microsoft.com/download/dotnet-framework-runtime/net472)

O [.NET Framework 4.7.2](https://dotnet.microsoft.com/download/dotnet-framework-runtime/net472) pode ser usado para executar aplicativos criados para as versões 4.0 a 4.7.1 do .NET Framework.

Instale o [.NET Framework 4.7.2](https://dotnet.microsoft.com/download/dotnet-framework-runtime/net472) no:

* Windows 10 Fall Creators Update (versão 1709)
* No Windows 10 Creators Update (versão 1703)
* Na Atualização de Aniversário do Windows 10 (versão 1607)
* Windows Server, versão 1709
* Windows Server 2016

O .NET Framework 4.7.2 não é compatível com o:

* Com o Windows 10 1507
* Com o Windows 10 1511

Se estiver usando o Windows 10 1507 ou 1511 e desejar instalar o .NET Framework 4.7.2, primeiro, você precisará atualizar para uma versão posterior do Windows 10.

## <a name="net-framework-462"></a>.NET Framework 4.6.2

O [.NET Framework 4.6.2](https://www.microsoft.com/en-us/download/details.aspx?id=53345) é a versão mais recente do .NET Framework compatível com o Windows 10 1507 e o 1511.

O .NET Framework 4.6.2 é compatível com aplicativos compilados para as versões 4.0 até 4.6.2 do .NET Framework.

## <a name="net-framework-35"></a>.NET Framework 3,5

Siga as instruções para instalar o [.NET Framework 3.5 no Windows 10](dotnet-35-windows-10.md).

O .NET Framework 3.5 é compatível com aplicativos compilados para as versões 1.0 até 3.5 do .NET Framework.

## <a name="additional-information"></a>Informações adicionais

As versões 4.x do .NET Framework são atualizações in-loco de versões anteriores. Isso significa o seguinte:

- Você pode ter somente uma versão do .NET Framework 4. x instalada em seu computador.

- Você não poderá instalar uma versão anterior do .NET Framework em seu computador se uma versão mais recente já tiver sido instalada.

- As versões 4.x do .NET Framework podem ser usadas para executar aplicativos compilados para o .NET Framework 4.0 por meio dessa versão. Por exemplo, .NET Framework 4.7 pode ser usado para executar aplicativos compilados para as versões 4.0 até 4.7 do .NET Framework. A versão mais recente (.NET Framework 4.7.2) pode ser usada para executar aplicativos compilados para todas as versões do .NET Framework da 4.0 em diante.

Para obter uma lista de todas as versões do .NET Framework disponíveis para download, consulte a página [Downloads do .NET](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral).

## <a name="help"></a>Ajuda

Se não for possível instalar a versão correta do .NET Framework, [entre em contato com a Microsoft para obter ajuda](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help).

## <a name="see-also"></a>Consulte também

- [Downloads do .NET](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral)
- [Solução de problemas de instalações e desinstalações bloqueadas do .NET Framework](troubleshoot-blocked-installations-and-uninstallations.md)
- [Instalar o .NET Framework para desenvolvedores](guide-for-developers.md)
