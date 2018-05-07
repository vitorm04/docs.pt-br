---
title: Interface IEnumReferenceIdentity
ms.date: 03/30/2017
api_name:
- IEnumReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumReferenceIdentity
helpviewer_keywords:
- IEnumReferenceIdentity interface [.NET Framework fusion]
ms.assetid: a17b3155-7216-4e16-8c9f-abce21f549e7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ebc9fe36955bac8b93ec95e9a55fc8ac1197d9a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="ienumreferenceidentity-interface"></a>Interface IEnumReferenceIdentity
Serve como um enumerador para uma coleção de `IReferenceIdentity` objetos.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|Obtém um ponteiro de interface para um novo `IEnumReferenceIdentity` que contém os mesmos membros este `IEnumReferenceIdentity`.|  
|`IEnumReferenceIdentity::Next`|Obtém o número especificado de `IReferenceIdentity` objetos, começando na posição atual.|  
|`IEnumReferenceIdentity::Reset`|Move o ponteiro de instrução para o início deste `IEnumReferenceIdentity`.|  
|`IEnumReferenceIdentity::Skip`|Move o ponteiro de instrução para frente pelo número especificado de elementos, começando na posição atual.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Isolation.h  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [Interface IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
