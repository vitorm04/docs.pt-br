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
ms.openlocfilehash: 15900fab59d172ada67d8aefeab698e1b44f808e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794386"
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a>Método ICorDebugHeapValue3::GetMonitorEventWaitList
Fornece uma lista ordenada de threads que são enfileirados no evento que está associado a um bloqueio de monitor.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ppThreadEnum`  
 fora O enumerador ICorDebugThreadEnum que fornece a lista ordenada de threads.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|A lista não está vazia.|  
|S_FALSE|A lista está vazia.|  
  
## <a name="exceptions"></a>Exceções  
  
## <a name="remarks"></a>Comentários  
 O primeiro thread na lista é o primeiro thread que é liberado pela próxima chamada para <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>. O próximo thread na lista é liberado na chamada a seguir e assim por diante.  
  
 Se a lista não estiver vazia, esse método retornará S_OK. Se a lista estiver vazia, o método retornará S_FALSE; Nesse caso, a enumeração ainda é válida, embora esteja vazia.  
  
 Em ambos os casos, a interface de enumeração é utilizável somente pela duração do estado atual sincronizado. No entanto, as interfaces do thread dispensadas a partir dela são válidas até que o thread saia.  
  
 Se `ppThreadEnum` não for um ponteiro válido, o resultado será indefinido.  
  
 Se ocorrer um erro de modo que não possa ser determinado que, se houver, os threads estão aguardando o monitor, o método retornará um HRESULT que indica falha.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
