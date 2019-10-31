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
ms.openlocfilehash: b6fd3682290c9752125aed7b9663c6704ade25de
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132330"
---
# <a name="cor_heapinfo-structure"></a>Estrutura COR_HEAPINFO
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
|`areGCStructuresValid`|`true` se as estruturas de coleta de lixo forem válidas e o heap puder ser enumerado; caso contrário, `false`.|  
|`pointerSize`|O tamanho, em bytes, dos ponteiros na arquitetura de destino.|  
|`numHeaps`|O número de heaps de coleta de lixo lógico no processo.|  
|`concurrent`|`TRUE` se a coleta de lixo (em segundo plano) simultânea está habilitada; caso contrário, `FALSE`.|  
|`gcType`|Um membro da enumeração [CorDebugGCType](cordebuggctype-enumeration.md) que indica se o coletor de lixo está em execução em uma estação de trabalho ou em um servidor.|  
  
## <a name="remarks"></a>Comentários  
 Uma instância da estrutura de `COR_HEAPINFO` é retornada chamando o método [ICorDebugProcess5:: GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) .  
  
 Antes de enumerar objetos no heap de coleta de lixo, você deve sempre verificar o campo `areGCStructuresValid` para garantir que o heap esteja em um estado enumerável. Para obter mais informações, consulte o método [ICorDebugProcess5:: GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) .  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Estruturas de depuração](debugging-structures.md)
- [Depuração](index.md)
