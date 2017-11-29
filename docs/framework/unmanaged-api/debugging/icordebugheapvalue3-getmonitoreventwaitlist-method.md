---
title: "Método ICorDebugHeapValue3::GetMonitorEventWaitList"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue3.GetMonitorEventWaitList
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue3::GetMonitorEventWaitList
helpviewer_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList method [.NET Framework debugging]
- GetMonitorEventWaitList method [.NET Framework debugging]
ms.assetid: 035a9035-ac66-4953-b48a-99652b42b7fe
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2624a5dcd2179f35567d19e33e4f981c5d049063
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
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
 [Interfaces de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
