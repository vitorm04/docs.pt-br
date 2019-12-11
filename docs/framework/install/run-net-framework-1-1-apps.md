---
title: Executar aplicativos do .NET Framework 1.1 no Windows 8, Windows 8.1 ou Windows 10
ms.date: 05/26/2017
helpviewer_keywords:
- Windows 8, running .NET Framework 1.1 apps
- .NET Framework 1.1, running on Windows 8
ms.assetid: fb14e195-fea5-4561-b9a8-60a67283edb9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1364eebf4d94a117a3ee7f0912b6ff4090e93853
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960037"
---
# <a name="run-net-framework-11-apps-on-windows-8-windows-81-or-windows-10"></a>Executar aplicativos do .NET Framework 1.1 no Windows 8, Windows 8.1 ou Windows 10

O .NET Framework 1,1 não tem suporte nos sistemas operacionais Windows 8, Windows 8.1, Windows Server 2012, [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)]ou Windows 10. Em alguns casos, o .NET Framework 1.1 é especificamente identificado conforme necessário para um aplicativo ser executado. Nesses casos, entre em contato com seu ISV (fornecedor independente de software) para que o aplicativo seja atualizado para execução no .NET Framework 3.5 SP1 ou versões posteriores. Para saber mais, confira [Migrar do .NET Framework 1.1](../migration-guide/migrating-from-the-net-framework-1-1.md).

## <a name="install-the-net-framework-11-from-a-cd-or-download-center"></a>Instalar o .NET Framework 1.1 de um CD ou do Centro de Download

Não é possível instalar manualmente o .NET Framework 1,1 no Windows 8, Windows 8.1, Windows Server 2012, [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)]ou Windows 10. Ele não é mais compatível. Se você tentar instalar o pacote, a seguinte mensagem de erro será exibida: "A instalação não pode continuar porque esta versão do .NET Framework é incompatível com a instalada anteriormente." Para resolver esse problema, instale o [.NET Framework 3.5 SP1](https://www.microsoft.com/download/details.aspx?id=22). Esta versão inclui o .NET Framework 2,0 (a versão que segue o .NET Framework 1,1), que tem suporte no Windows 8, Windows 8.1 e Windows 10. Você sempre deve tentar instalar o aplicativo primeiro para determinar se ele será atualizado automaticamente para uma versão posterior do .NET Framework. Caso contrário, entre em contato com seu ISV para obter uma atualização do aplicativo.

## <a name="see-also"></a>Consulte também

- [Migrando do .NET Framework 1.1](../migration-guide/migrating-from-the-net-framework-1-1.md)
- [Instalar o .NET Framework 3.5 no Windows 10, no Windows 8.1 e no Windows 8](dotnet-35-windows-10.md)
