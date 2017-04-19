---
title: Compatibilidade de aplicativos no .NET Framework 4.6.1 | Microsoft Docs
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
- application compatibility,.NET Framework
- application compatibility,.NET Framework 4.6.1
ms.assetid: b86cc4ad-6a9e-4246-aa96-5aae319d9d55
caps.latest.revision: 7
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 95c8e4d38a9a4770813db141d76d33e10e34cc12
ms.lasthandoff: 04/18/2017

---
# <a name="application-compatibility-in-the-net-framework-461"></a>Compatibilidade de aplicativos no .NET Framework 4.6.1
Este tópico fornece links para informações sobre problemas de compatibilidade do aplicativo entre o .NET Framework 4.6 e o [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]. Os problemas se enquadram em duas categorias:  
  
 [Alterações no tempo de execução](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6-1.md)  
 As alterações feitas no tempo de execução afetam todos os aplicativos em execução no [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] e que usem um determinado recurso.  
  
 [Alterações de redirecionamento](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)  
 As alterações de redirecionamento afetam apenas os aplicativos recompilados para direcionar especificamente para o [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]. Os aplicativos destinados a versões anteriores do .NET Framework se comportam como antes durante a execução nessas versões.  
  
 Nos itens que descrevem alterações feitas no de tempo de execução e de redirecionamento, classificamos itens individuais pelo impacto esperado, da seguinte forma:  
  
 Principal  
 Esta é uma alteração significativa que afeta um grande número de aplicativos ou que exige a modificação significativa do código.  
  
 Secundário  
 Esta é uma alteração que afeta um pequeno número de aplicativos ou que exige a modificação secundária do código.  
  
 Caso de borda  
 Esta é uma alteração que afeta aplicativos em cenários muito específicos que não são comuns.  
  
 Transparente  
 Esta é uma alteração que não tem efeito visível para o desenvolvedor ou o usuário do aplicativo. O aplicativo não deve exigir modificação por conta dessa alteração.  
  
## <a name="see-also"></a>Consulte também  
 [Compatibilidade de aplicativos](../../../docs/framework/migration-guide/application-compatibility.md)
