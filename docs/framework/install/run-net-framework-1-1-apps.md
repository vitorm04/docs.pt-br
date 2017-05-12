---
title: Executar aplicativos do .NET Framework 1.1 no Windows 8, Windows 8.1 ou Windows 10 | Microsoft Docs
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows 8, running .NET Framework 1.1 apps
- .NET Framework 1.1, running on Windows 8
ms.assetid: fb14e195-fea5-4561-b9a8-60a67283edb9
caps.latest.revision: 9
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: f63c5c09bef5e1d2674652f19af0468fd2dd06ac
ms.contentlocale: pt-br
ms.lasthandoff: 05/11/2017

---
# <a name="running-net-framework-11-apps-on-windows-8-windows-81-or-windows-10"></a>Executando aplicativos do .NET Framework 1.1 no Windows 8, Windows 8.1 ou Windows 10
O .NET Framework 1.1 não é compatível no [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)] ou nos sistemas operacionais Windows 10 . Em alguns casos, o .NET Framework 1.1 é especificamente identificado conforme necessário para um aplicativo ser executado. Nesses casos, você deve entrar em contato com seu ISV (fornecedor independente de software) para que o aplicativo fosse atualizado para execução no [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] ou em uma versão posterior. Para saber mais, confira [Migrar do .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md).  
  
## <a name="installing-the-net-framework-11-from-a-cd-or-download-center"></a>Instalando o .NET Framework 1.1 com um CD ou no Centro de Download  
 Não é possível instalar manualmente o .NET Framework 1.1 no [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)] ou Windows 10. Ele não é mais compatível. Se você tentar instalar o pacote, a seguinte mensagem de erro será exibida: "A instalação não pode continuar porque esta versão do .NET Framework é incompatível com a instalada anteriormente." Para resolver esse problema, instale o [.NET Framework 3.5 SP1](http://www.microsoft.com/download/details.aspx?id=22). Essa versão inclui o .NET Framework 2.0 (a versão após o .NET Framework 1.1), compatível no [!INCLUDE[win8](../../../includes/win8-md.md)], no [!INCLUDE[win81](../../../includes/win81-md.md)] e no Windows 10. Você sempre deve tentar instalar o aplicativo para determinar primeiro se ele será atualizado automaticamente para uma versão posterior ao .NET Framework. Caso contrário, entre em contato com seu ISV para obter uma atualização do aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [Migrar do .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)   
 [Instalação do .NET Framework 3.5 no Windows 8 e versões posteriores](../../../docs/framework/install/net-framework-3-5-on-windows-8-plus.md)
