---
title: Método ICorDebugHeapValue3::GetMonitorEventWaitList
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3.GetMonitorEventWaitList
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList
helpviewer_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList method [.NET Framework debugging]
- GetMonitorEventWaitList method [.NET Framework debugging]
ms.assetid: 035a9035-ac66-4953-b48a-99652b42b7fe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 27815cf8cb7fdcd1c01f26391c317d52bbb388ca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628507"
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a>Método ICorDebugHeapValue3::GetMonitorEventWaitList
Fornece uma lista ordenada de threads que estão na fila o evento que está associado com um bloqueio do monitor.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppThreadEnum`  
 [out] O enumerador ICorDebugThreadEnum que fornece a lista ordenada de threads.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|A lista não está vazia.|  
|S_FALSE|A lista está vazia.|  
  
## <a name="exceptions"></a>Exceções  
  
## <a name="remarks"></a>Comentários  
 O primeiro thread na lista é o primeiro thread que é lançado pela próxima chamada para <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>. O próximo thread na lista é liberado na chamada a seguir e assim por diante.  
  
 Se a lista não estiver vazia, esse método retorna S_OK. Se a lista estiver vazia, o método retorna S_FALSE; Nesse caso, a enumeração é ainda é válida, embora ele está vazio.  
  
 Em ambos os casos, a interface de enumeração é utilizável apenas para a duração do estado atual de sincronizado. No entanto, as interfaces do thread liberadas dele são válidos até que o thread seja encerrado.  
  
 Se `ppThreadEnum` não for um ponteiro válido, o resultado será indefinido.  
  
 Se ocorrer um erro, de modo que ele não pode ser determinado que, se houver, segmentos estão aguardando o monitor, o método retorna um HRESULT que indica falha.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
