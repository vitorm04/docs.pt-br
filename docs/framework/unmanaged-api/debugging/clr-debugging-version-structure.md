---
title: Estrutura CLR_DEBUGGING_VERSION
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_VERSION
helpviewer_keywords:
- CLR_DEBUGGING_VERSION structure [.NET Framework debugging]
ms.assetid: 4d821186-3ddf-405a-ac44-d79438a9f7f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4528ccd77fed2ea2a9b2d08243ffa1535bfad1ae
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274083"
---
# <a name="clr_debugging_version-structure"></a>Estrutura CLR_DEBUGGING_VERSION
Define a versão do produto do CLR (Common Language Runtime) para fins de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct _CLR_DEBUGGING_VERSION  
{  
    WORD wStructVersion;
    WORD wMajor;
    WORD wMinor;
    WORD wBuild;
    WORD wRevision;
} CLR_DEBUGGING_VERSION;
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`wStructVersion`|O número de versão da estrutura|  
|`wMajor`|O número da versão principal.|  
|`wMinor`|O número da versão secundária.|  
|`wBuild`|O número de build.|  
|`wRevision`|O número de revisão.|  
  
## <a name="remarks"></a>Comentários  
 A `CLR_DEBUGGING_VERSION` estrutura é igual à estrutura COR_VERSION, no entanto, a `CLR_DEBUGGING_VERSION` estrutura fornece um campo de versão de estrutura`wStructVersion`adicional (). No momento, esse campo deve ser definido como zero.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl  
  
 **Biblioteca** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Estruturas de depuração](debugging-structures.md)
- [Depuração](index.md)
