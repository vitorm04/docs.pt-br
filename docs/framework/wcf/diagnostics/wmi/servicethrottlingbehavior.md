---
title: ServiceThrottlingBehavior
ms.date: 03/30/2017
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
ms.openlocfilehash: 9a7fbf93dbdbf1a6debcf865b4883b5784e2ff4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="servicethrottlingbehavior"></a>ServiceThrottlingBehavior
ServiceThrottlingBehavior  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe ServiceThrottlingBehavior não define nenhum método.  
  
## <a name="properties"></a>Propriedades  
 A classe ServiceThrottlingBehavior tem as seguintes propriedades:  
  
### <a name="maxconcurrentcalls"></a>maxConcurrentCalls  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 O número máximo de mensagens processando ativamente entre todos os objetos do distribuidor em um ServiceHost.  
  
### <a name="maxconcurrentinstances"></a>MaxConcurrentInstances  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 O número máximo de objetos de serviço que podem ser executados ao mesmo tempo.  
  
### <a name="maxconcurrentsessions"></a>MaxConcurrentSessions  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 O número máximo de sessões que um host pode aceitar de cada vez.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
