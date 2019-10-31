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
ms.openlocfilehash: 1305b9ebe3cd87ba002ee87610ff309d015a44e6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131743"
---
# <a name="ienumreferenceidentity-interface"></a>Interface IEnumReferenceIdentity
Serve como um enumerador para uma coleção de objetos `IReferenceIdentity`.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|Obtém um ponteiro de interface para um novo `IEnumReferenceIdentity` que contém os mesmos membros que este `IEnumReferenceIdentity`.|  
|`IEnumReferenceIdentity::Next`|Obtém o número especificado de objetos de `IReferenceIdentity`, começando na posição atual.|  
|`IEnumReferenceIdentity::Reset`|Move o ponteiro de instrução para o início deste `IEnumReferenceIdentity`.|  
|`IEnumReferenceIdentity::Skip`|Move o ponteiro de instrução para frente pelo número especificado de elementos, começando na posição atual.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** Isolamento. h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interfaces de fusão](fusion-interfaces.md)
- [Interface IReferenceIdentity](ireferenceidentity-interface.md)
