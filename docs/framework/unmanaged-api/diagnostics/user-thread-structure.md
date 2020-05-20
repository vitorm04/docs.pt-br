---
title: Estrutura USER_THREAD
ms.date: 03/30/2017
api_name:
- USER_THREAD
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- USER_THREAD
helpviewer_keywords:
- USER_THREAD structure [.NET Framework debugging]
ms.assetid: a57c7d71-c4b0-41f9-a964-0c5ee84a3124
topic_type:
- apiref
ms.openlocfilehash: 5144feab742bc5dac36563d701d81a699d0bb2f3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609437"
---
# <a name="user_thread-structure"></a>Estrutura USER_THREAD
Fornece informações para um depurador sobre um thread. Para obter mais informações, consulte o método [INotifySource2:: SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`pSidBuffer`|Endereço do buffer de thread.|  
|`dwSidLen`|Comprimento do buffer de thread, em bytes.|  
|`dwTid`|ID do thread.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** ProtocolNotify2. idl  
  
## <a name="see-also"></a>Confira também

- [Método SetNotifyFilter](inotifysource2-setnotifyfilter-method.md)
- [Estruturas de armazenamento de símbolo de diagnóstico](diagnostics-symbol-store-structures.md)
