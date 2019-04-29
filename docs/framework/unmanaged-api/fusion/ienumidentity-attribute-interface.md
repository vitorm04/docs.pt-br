---
title: Interface IEnumIDENTITY_ATTRIBUTE
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d725228f2a7359d415673fdcb90d0cabae1a40be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697326"
---
# <a name="ienumidentityattribute-interface"></a>Interface IEnumIDENTITY_ATTRIBUTE
Serve como um enumerador para os atributos do objeto de código no escopo atual.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|Obtém um ponteiro de interface para um novo `IEnumIDENTITY_ATTRIBUTE` que contém os mesmos membros que isso `IEnumIDENTITY_ATTRIBUTE`.|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|Grava os dados contidos em elementos deste `IEnumIDENTITY_ATTRIBUTE` no buffer de dados especificado.|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|Obtém o número especificado de atributos, começando na posição atual.|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|Move o ponteiro de instrução para o início deste `IEnumIDENTITY_ATTRIBUTE`.|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|Move o ponteiro de instrução para frente pelo número especificado de elementos, começando na posição atual.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Isolation.h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interfaces de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
