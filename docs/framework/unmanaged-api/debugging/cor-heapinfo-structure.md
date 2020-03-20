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
ms.openlocfilehash: 37659262695b63a6dd6390c62c4bb7e04fdadca4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179302"
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
|`areGCStructuresValid`|`true`se as estruturas de coleta de lixo forem válidas e o monte puder ser enumerado; caso contrário, `false`.|  
|`pointerSize`|O tamanho, em bytes, de ponteiros na arquitetura alvo.|  
|`numHeaps`|O número de montes lógicos de coleta de lixo no processo.|  
|`concurrent`|`TRUE`se a coleta de lixo simultânea (fundo) estiver habilitada; caso contrário, `FALSE`.|  
|`gcType`|Um membro da [enumeração CorDebugGCType](cordebuggctype-enumeration.md) que indica se o coletor de lixo está sendo executado em uma estação de trabalho ou em um servidor.|  
  
## <a name="remarks"></a>Comentários  
 Uma instância `COR_HEAPINFO` da estrutura é devolvida chamando o método [ICorDebugProcess5::GetGCHeapInformation.](icordebugprocess5-getgcheapinformation-method.md)  
  
 Antes de enumerar objetos no monte de `areGCStructuresValid` coleta de lixo, você deve sempre verificar o campo para garantir que o monte esteja em um estado enumerado. Para obter mais informações, consulte o método [ICorDebugProcess5::GetGCHeapInformation.](icordebugprocess5-getgcheapinformation-method.md)  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Estruturas de depuração](debugging-structures.md)
- [Depuração](index.md)
