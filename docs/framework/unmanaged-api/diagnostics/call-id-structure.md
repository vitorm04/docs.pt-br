---
title: Estrutura CALL_ID
ms.date: 03/30/2017
api_name:
- CALL_ID
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- CALL_ID
helpviewer_keywords:
- CALL_ID structure [.NET Framework debugging]
ms.assetid: bfd46324-afec-4782-9c18-586d81fb4740
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 204c2dfbf28f95c1b8c2d2c1b757730e64a8e91d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54503695"
---
# <a name="callid-structure"></a>Estrutura CALL_ID
Fornece informações para um depurador sobre uma função que está sendo chamado. Consulte a [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) interface para obter mais informações.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef struct tagCALL_ID  
{  
    LPCOLESTR       szMachine;  
    DWORD           dwPid;  
    USER_THREAD     *pUserThread;  
    STACK_ADDRESS   addrStackPointer;  
    LPCOLESTR       szEntryPoint;  
    LPCOLESTR       szDestinationMachine;  
} CALL_ID;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`szMachine`|Identifica o computador que está fazendo a chamada.|  
|`dwPid`|Identifica o processador de máquina.|  
|`pUserThread`|Identifica o thread que está executando a chamada.|  
|`addrStackPointer`|Especifica o endereço da pilha de chamadas.|  
|`szEntryPoint`|Especifica o endereço da chamada.|  
|`szDestinationMachine`|Identifica o computador que executará a chamada.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** ProtocolNotify2.idl  
  
## <a name="see-also"></a>Consulte também
- [Interface INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [Estruturas de repositório de símbolos de diagnóstico](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
