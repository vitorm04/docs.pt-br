---
title: Compatibilidade de aplicativos no .NET Framework 4.6.2 | Microsoft Docs
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application compatibility,.NET Framework
- application compatibility,.NET Framework 4,6,2
ms.assetid: bdb8335a-a63f-43bb-b978-c1ee92870033
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: e34651e87e9c1ccc58472910c0340987da7fc973
ms.lasthandoff: 04/18/2017

---
# <a name="application-compatibility-in-the-net-framework-462"></a>Compatibilidade de aplicativos no .NET Framework 4.6.2
Este tópico fornece links para informações sobre problemas de compatibilidade de aplicativos entre o .NET Framework 4.6.1 e o 4.6.2. Os problemas se enquadram em duas categorias:  
  
 [Alterações no tempo de execução](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6-2.md)  
 As alterações feitas no tempo de execução afetam todos os aplicativos em execução no [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] e que usem um determinado recurso.  
  
 [Alterações de redirecionamento](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)  
 As alterações de redirecionamento afetam aplicativos recompilados para segmentar o [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]. Entre elas estão:  
  
-   Alterações feitas no ambiente de tempo de design. Por exemplo, as ferramentas de compilação podem emitir avisos quando antes não faziam isso.  
  
-   Alterações feitas no ambiente de tempo de execução. Elas afetam apenas os aplicativos destinados especificamente ao [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]. Os aplicativos destinados a versões anteriores do .NET Framework se comportam como antes durante a execução nessas versões.  
  
 No tópico que descreve alterações de redirecionamento, classificamos itens individuais pelo impacto esperado, da seguinte forma:  
  
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
 [Compatibilidade de aplicativos no 4.5.1](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-1.md)   
 [Compatibilidade de aplicativos no 4.5.2](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-2.md)   
 [Compatibilidade de aplicativos no 4.5](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5.md)   
 [Compatibilidade de aplicativos no 4.6](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6.md)   
 [Compatibilidade de aplicativos no 4.6.1](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)   
 [Compatibilidade de aplicativos](../../../docs/framework/migration-guide/application-compatibility.md)   
 [Lista de alterações do .NET 4.6.2 no GitHub](http://go.microsoft.com/fwlink/?LinkId=708778)
 
