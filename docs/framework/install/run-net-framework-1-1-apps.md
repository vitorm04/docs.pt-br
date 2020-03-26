---
title: Executar aplicativos do .NET Framework 1.1 no Windows 8, Windows 8.1 ou Windows 10
description: Descreve como acomodar aplicativos que requerem .NET Framework 1.1, que não é mais suportado em muitas versões do sistema operacional Windows.
ms.date: 05/26/2017
helpviewer_keywords:
- Windows 8, running .NET Framework 1.1 apps
- .NET Framework 1.1, running on Windows 8
ms.assetid: fb14e195-fea5-4561-b9a8-60a67283edb9
ms.openlocfilehash: 6d1cb2f9251bba96d0a378bf4dbab9f7da267037
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111784"
---
# <a name="run-net-framework-11-apps-on-windows-8-windows-81-or-windows-10"></a>Executar aplicativos do .NET Framework 1.1 no Windows 8, Windows 8.1 ou Windows 10

O .NET Framework 1.1 não é suportado nos sistemas operacionais Windows 8, Windows 8.1, Windows Server 2012, Windows Server 2012 R2 ou Windows 10. Em alguns casos, o .NET Framework 1.1 é necessário para que um aplicativo seja executado. Nesses casos, entre em contato com o seu fornecedor de software independente (ISV) para que o aplicativo seja atualizado para ser executado no .NET Framework 3.5 SP1 ou em uma versão posterior. Para obter mais informações, consulte [Migrando do Quadro .NET 1.1](../migration-guide/migrating-from-the-net-framework-1-1.md).

## <a name="install-net-framework-11-from-a-cd-or-download-center"></a>Instale o .NET Framework 1.1 a partir de um CD ou centro de download

Não é possível instalar manualmente o .NET Framework 1.1 no Windows 8, Windows 8.1, Windows Server 2012, Windows Server 2012 R2 ou Windows 10 a partir de um CD ou centro de download. Não é mais suportado. Se você tentar instalar o pacote, a seguinte mensagem de erro será exibida: "A instalação não pode continuar porque esta versão do .NET Framework é incompatível com a instalada anteriormente." Para resolver esse problema, instale [o .NET Framework 3.5 SP1](https://www.microsoft.com/download/details.aspx?id=22). Esta versão inclui o .NET Framework 2.0 (a versão que segue o .NET Framework 1.1), que é suportado no Windows 8, Windows 8.1 e Windows 10. Você deve sempre tentar instalar o aplicativo primeiro para determinar se ele será atualizado automaticamente para uma versão posterior do .NET Framework. Caso isso não aconteça, entre em contato com seu ISV para obter uma atualização do aplicativo.

## <a name="see-also"></a>Confira também

- [Migrar do .NET Framework 1.1](../migration-guide/migrating-from-the-net-framework-1-1.md)
- [Instalar o .NET Framework 3.5 no Windows 10, Windows 8.1 e Windows 8](dotnet-35-windows-10.md)
