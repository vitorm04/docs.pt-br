---
title: Compatibilidade de aplicativos no .NET Framework 4.6 | Microsoft Docs
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
- application compatibility, .NET Framework
- application compatibility. NET Framework 4.6
ms.assetid: 7a3fd352-a8ba-4f9a-8250-951f2c994248
caps.latest.revision: 7
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 32bbbf7cb9acd71f5b8e28b7b12aab706221fab9
ms.lasthandoff: 04/18/2017

---
# <a name="application-compatibility-in-the-net-framework-46"></a>Compatibilidade do aplicativo no .NET Framework 4.6
Este tópico fornece links para informações sobre problemas de compatibilidade de aplicativos entre o .NET Framework 4.5.2 e o 4.6. Os problemas são divididos em duas categorias:  
  
 [Alterações no tempo de execução](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)  
 As alterações feitas no tempo de execução afetam todos os aplicativos em execução no [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] e que usem um determinado recurso.  
  
 [Alterações de redirecionamento](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)  
 As alterações de redirecionamento afetam aplicativos que estão recompilados para serem redirecionados ao .NET Framework 4.5, 4.5.1 ou 4.5.2 ou 4.6. Entre elas estão:  
  
-   Alterações feitas no ambiente de tempo de design. Por exemplo, as ferramentas de compilação podem emitir avisos quando antes não faziam isso.  
  
-   Alterações feitas no ambiente de tempo de execução. Elas afetam apenas os aplicativos destinados especificamente ao [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]. Os aplicativos destinados a versões anteriores do .NET Framework se comportam como antes durante a execução nessas versões.  
  
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
 [Compatibilidade de aplicativos no 4.5.2](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-2.md)
