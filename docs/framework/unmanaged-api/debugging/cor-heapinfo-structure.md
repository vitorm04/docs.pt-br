---
title: Estrutura COR_HEAPINFO
ms.date: 03/30/2017
api_name:
- COR_HEAPINFO
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPINFO
helpviewer_keywords:
- COR_HEAPINFO structure [.NET Framework debugging]
ms.assetid: bfb2cd39-3e0b-4d51-ba0c-f009755c1456
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3dd233643bd18b60b7d6176c34ee57e4061daf7c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740659"
---
# <a name="corheapinfo-structure"></a>Estrutura COR_HEAPINFO
Fornece informações gerais sobre o heap de coleta de lixo, incluindo se é enumerável.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;   
    DWORD pointerSize;   
    DWORD numHeaps;  
    BOOL concurrent;   
    CorDebugGCType gcType;   
} COR_HEAPINFO;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`areGCStructuresValid`|`true` Se as estruturas de coleta de lixo são válidas e o heap pode ser enumerado; Caso contrário, `false`.|  
|`pointerSize`|O tamanho, em bytes, dos ponteiros na arquitetura de destino.|  
|`numHeaps`|O número de coleta de lixo lógico heaps no processo.|  
|`concurrent`|`TRUE` Se simultâneas a coleta de lixo (em segundo plano) estiver habilitada; Caso contrário, `FALSE`.|  
|`gcType`|Um membro do [CorDebugGCType](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md) enumeração que indica se o coletor de lixo está em execução em uma estação de trabalho ou um servidor.|  
  
## <a name="remarks"></a>Comentários  
 Uma instância das `COR_HEAPINFO` estrutura é retornada ao chamar o [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) método.  
  
 Antes de enumerar os objetos no heap de coleta de lixo, você sempre deve verificar o `areGCStructuresValid` campo para garantir que o heap está em um estado enumerável. Para obter mais informações, consulte o [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Estruturas de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
