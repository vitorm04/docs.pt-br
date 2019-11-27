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
ms.openlocfilehash: 51db7a2b6464b562e09ce061991898a8d604ead1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437973"
---
# <a name="user_thread-structure"></a>Estrutura USER_THREAD
Fornece informações para um depurador sobre um thread. Para obter mais informações, consulte o método [INotifySource2:: SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) .  
  
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
  
|{1&gt;Membro&lt;1}|Descrição|  
|------------|-----------------|  
|`pSidBuffer`|Endereço do buffer de thread.|  
|`dwSidLen`|Comprimento do buffer de thread, em bytes.|  
|`dwTid`|ID do thread.|  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Cabeçalho:** ProtocolNotify2. idl  
  
## <a name="see-also"></a>Consulte também

- [Método SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)
- [Estruturas de repositório de símbolos de diagnóstico](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
