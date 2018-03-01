---
title: "Método ICorDebugHeapValue3::GetMonitorEventWaitList"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a4112188ff069184cab998f5bbd0fc70d1ce7dc9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a>Método ICorDebugHeapValue3::GetMonitorEventWaitList
Fornece uma lista ordenada de threads que estão em fila o evento que está associado com um bloqueio do monitor.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppThreadEnum`  
 [out] O enumerador de ICorDebugThreadEnum que fornece a lista ordenada de threads.  
  
## <a name="return-value"></a>Valor de retorno  
 Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|A lista não está vazia.|  
|S_FALSE|A lista está vazia.|  
  
## <a name="exceptions"></a>Exceções  
  
## <a name="remarks"></a>Comentários  
 O primeiro thread na lista é o primeiro thread lançado pela próxima chamada para <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>. O próximo segmento na lista é liberado na chamada a seguir e assim por diante.  
  
 Se a lista não estiver vazia, esse método retorna S_OK. Se a lista estiver vazia, o método retornará S_FALSE; Nesse caso, a enumeração ainda é válida, embora ela está vazia.  
  
 Em ambos os casos, a interface de enumeração é útil apenas para a duração do estado sincronizado atual. No entanto, interfaces do thread liberados dele são válidas até que o thread será encerrado.  
  
 Se `ppThreadEnum` não é um ponteiro válido, o resultado é indefinido.  
  
 Se ocorrer um erro, de modo que ele não pode ser determinado que, se houver, os threads estão esperando para o monitor, o método retorna um HRESULT que indica falha.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
