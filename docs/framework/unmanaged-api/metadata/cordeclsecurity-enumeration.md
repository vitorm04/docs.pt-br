---
title: "Enumeração CorDeclSecurity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDeclSecurity
api_location: mscoree.dll
api_type: COM
f1_keywords: CorDeclSecurity
helpviewer_keywords: CorDeclSecurity enumeration [.NET Framework metadata]
ms.assetid: 864f1267-d267-4696-8df7-1f83f8444d6f
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 30fd7ca2cf7962c6cadb43d4d8e3031b59292463
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="cordeclsecurity-enumeration"></a>Enumeração CorDeclSecurity
Especifica as ações de segurança que podem ser executadas usando a segurança declarativa.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum CorDeclSecurity {  
  
    dclActionMask               =   0x001f,  
    dclActionNil                =   0x0000,  
    dclRequest                  =   0x0001,  
    dclDemand                   =   0x0002,  
    dclAssert                   =   0x0003,  
    dclDeny                     =   0x0004,  
    dclPermitOnly               =   0x0005,  
    dclLinktimeCheck            =   0x0006,  
    dclInheritanceCheck         =   0x0007,  
    dclRequestMinimum           =   0x0008,  
    dclRequestOptional          =   0x0009,  
    dclRequestRefuse            =   0x000a,  
    dclPrejitGrant              =   0x000b,  
    dclPrejitDenied             =   0x000c,  
    dclNonCasDemand             =   0x000d,  
    dclNonCasLinkDemand         =   0x000e,  
    dclNonCasInheritance        =   0x000f,  
    dclLinkDemandChoice         =   0x0010,  
    dclInheritanceDemandChoice  =   0x0011,  
    dclDemandChoice             =   0x0012,  
    dclMaximumValue             =   0x0012  
  
} CorDeclSecurity;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`dclActionMask`|Reservado.|  
|`dclActionNil`|Reservado.|  
|`dclRequest`|Reservado.|  
|`dclDemand`|Todos os chamadores na pilha de chamadas deverão ter a permissão especificada pelo objeto de permissão atual.|  
|`dclAssert`|O código de chamada pode acessar o recurso identificado pelo objeto de permissão atual, mesmo que os chamadores mais acima na pilha não recebeu permissão para acessar o recurso|  
|`dclDeny`|A capacidade de acessar o recurso especificado pelo objeto atual da permissão é negada a chamadores, mesmo se eles têm permissão para acessá-lo.|  
|`dclPermitOnly`|Somente os recursos especificados por esse objeto de permissão poderão ser acessados, mesmo que o código tenha recebido permissão para acessar outros recursos.|  
|`dclLinktimeCheck`|O chamador imediato é necessário ter a permissão especificada para um determinado período de tempo.|  
|`dclInheritanceCheck`|A classe derivada herdar de outra classe ou substituindo um método é necessária para ter a permissão especificada.|  
|`dclRequestMinimum`|O chamador pode solicitar para as permissões mínimas necessárias para a execução de código. Esta ação só pode ser usada no escopo do assembly.|  
|`dclRequestOptional`|O chamador pode solicitar permissões adicionais que são opcionais (não é necessário para executar). Essa solicitação implicitamente recusa todas as outras permissões não especificamente solicitadas. Esta ação só pode ser usada no escopo do assembly.|  
|`dclRequestRefuse`|Solicitação do chamador para permissões que pode ser usado de forma incorreta não será concedida. Esta ação só pode ser usada no escopo do assembly.|  
|`dclPrejitGrant`|Reservado.|  
|`dclPrejitDenied`|Reservado.|  
|`dclNonCasDemand`|Reservado.|  
|`dclNonCasLinkDemand`|O chamador imediato deverá ter recebido a permissão especificada.|  
|`dclNonCasInheritance`|Reservado.|  
|`dclLinkDemandChoice`|Reservado.|  
|`dclInheritanceDemandChoice`|Reservado.|  
|`dclDemandChoice`|Reservado.|  
|`dclMaximumValue`|Reservado.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corhdr  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
