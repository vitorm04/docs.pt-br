---
title: Interface IEnumIDENTITY_ATTRIBUTE
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IEnumIDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumIDENTITY_ATTRIBUTE
helpviewer_keywords:
- IEnumIDENTITY_ATTRIBUTE interface [.NET Framework fusion]
ms.assetid: c2ec2748-e9ae-4e1b-80db-6fcec5cb81a1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fc77f2106f5063b8db25f375c354a15f9f936e78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ienumidentityattribute-interface"></a>Interface IEnumIDENTITY_ATTRIBUTE
Serve como um enumerador para os atributos do objeto de código no escopo atual.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|Obtém um ponteiro de interface para um novo `IEnumIDENTITY_ATTRIBUTE` que contém os mesmos membros este `IEnumIDENTITY_ATTRIBUTE`.|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|Grava os dados contidos em elementos deste `IEnumIDENTITY_ATTRIBUTE` para o buffer de dados especificado.|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|Obtém o número especificado de atributos, começando na posição atual.|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|Move o ponteiro de instrução para o início deste `IEnumIDENTITY_ATTRIBUTE`.|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|Move o ponteiro de instrução para frente pelo número especificado de elementos, começando na posição atual.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Isolation.h  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
