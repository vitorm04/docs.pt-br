---
title: Estrutura COR_VERSION
ms.date: 03/30/2017
api_name:
- COR_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_VERSION
helpviewer_keywords:
- COR_VERSION structure [.NET Framework debugging]
ms.assetid: 5efaee1c-a001-4c73-9525-4160f4c71567
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2668e36debebb5ba71277912f37833eba584fde
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="corversion-structure"></a>Estrutura COR_VERSION
Armazena o número da versão com quatro partes padrão do CLR.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`dwMajor`|O número da versão principal.|  
|`dwMinor`|O número da versão secundária.|  
|`dwBuild`|O número de build.|  
|`dwSubBuild`|O número de compilação sub.|  
  
## <a name="remarks"></a>Comentários  
 Se o número de versão é 1.0.3705.288, 1 é o número de versão principal, 0 é o número de versão secundária, 3705 é o número de compilação e 288 é o número de compilação sub.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
