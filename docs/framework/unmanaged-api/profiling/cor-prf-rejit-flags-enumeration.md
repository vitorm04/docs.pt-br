---
title: Enumeração COR_PRF_REJIT_FLAGS
ms.date: 08/06/2019
api_name:
- COR_PRF_REJIT_FLAGS Enumeration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_REJIT_FLAGS
helpviewer_keywords:
- COR_PRF_REJIT_FLAGS enumeration [.NET Framework profiling]
topic_type:
- apiref
author: davmason
ms.author: davmason
ms.openlocfilehash: 8fc5f1a488826d8adc6aecb8ef122609bebbe813
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177094"
---
# <a name="cor_prf_rejit_flags-enumeration"></a>Enumeração COR_PRF_REJIT_FLAGS
Contém valores que indicam como a API [ICorProfilerInfo10:RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) deve se comportar.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum  
{
    COR_PRF_REJIT_BLOCK_INLINING = 0x1,
    COR_PRF_REJIT_INLINING_CALLBACKS    = 0x2
} COR_PRF_REJIT_FLAGS;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`COR_PRF_REJIT_BLOCK_INLINING`| Os métodos rejitted serão impedidos de serem informais em outros métodos. |  
|`COR_PRF_REJIT_INLINING_CALLBACKS`| Receba `GetFunctionParameters` retornos de chamada para quaisquer métodos que inlineos os métodos solicitados para serem ReJITted. |  

## <a name="requirements"></a>Requisitos  
 **Plataformas:** Consulte [os sistemas operacionais suportados pelo .NET Core](../../../core/install/dependencies.md?pivots=os-windows).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]
  
## <a name="see-also"></a>Confira também

- [Criando perfil de enumerações](profiling-enumerations.md)
