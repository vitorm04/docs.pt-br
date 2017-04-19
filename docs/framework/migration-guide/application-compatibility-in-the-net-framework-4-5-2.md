---
title: Compatibilidade de aplicativos no .NET Framework 4.5.2 | Microsoft Docs
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
- application compatibility
- .NET Framework 4.5.2
- application compatibility,.NET Framework
- application compatibility,.NET Framework 4.5.2
ms.assetid: 4c6a029d-c565-4f25-b87b-b2361634bd74
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2631cb6c9464954b18cf97e21b8f48b30458c0db
ms.lasthandoff: 04/18/2017

---
# <a name="application-compatibility-in-the-net-framework-452"></a>Compatibilidade de aplicativos no .NET Framework 4.5.2
Este tópico fornece links para informações sobre problemas de compatibilidade do aplicativo entre o .NET Framework 4.5.1 e o 4.5.2. Os problemas são divididos em duas categorias:  
  
 [Alterações no tempo de execução](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-2.md)  
 As alterações no tempo de execução afetam todos os aplicativos que estão sendo executados no .NET Framework 4.5.2 e que usam um recurso específico.  
  
 [Alterações de redirecionamento](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-5-2.md)  
 As alterações de redirecionamento afetam aplicativos que estão recompilados para serem redirecionados ao .NET Framework 4.5, 4.5.1 ou 4.5.2. Entre elas estão:  
  
-   Alterações feitas no ambiente de tempo de design. Por exemplo, as ferramentas de compilação podem emitir avisos quando antes não faziam isso.  
  
-   Alterações feitas no ambiente de tempo de execução. Elas afetam apenas os aplicativos destinados especificamente ao .NET Framework 4.5.2. Os aplicativos destinados a versões anteriores do .NET Framework se comportam como antes durante a execução nessas versões.  
  
 Nos tópicos que descrevem alterações feitas no de tempo de execução e de redirecionamento, classificamos itens individuais pelo impacto esperado, da seguinte forma:  
  
 Principal  
 Esta é uma alteração significativa que afeta um grande número de aplicativos ou que exige a modificação significativa do código.  
  
 Secundário  
 Esta é uma alteração que afeta um pequeno número de aplicativos ou que exige a modificação secundária do código.  
  
 Caso de borda  
 Esta é uma alteração que afeta aplicativos em cenários muito específicos que não são comuns.  
  
 Transparente  
 Esta é uma alteração que não tem efeito visível para o desenvolvedor ou o usuário do aplicativo. O aplicativo não deve exigir modificação por conta dessa alteração.  
  
## <a name="see-also"></a>Consulte também  
 [Versões e dependências](../../../docs/framework/migration-guide/versions-and-dependencies.md)   
 [Compatibilidade de aplicativos](../../../docs/framework/migration-guide/application-compatibility.md)   
 [Compatibilidade de aplicativos no 4.5](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5.md)   
 [Compatibilidade de aplicativos no 4.5.1](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-1.md)
