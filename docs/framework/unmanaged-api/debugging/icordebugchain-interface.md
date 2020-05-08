---
title: Interface ICorDebugChain
ms.date: 03/30/2017
api_name:
- ICorDebugChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain
helpviewer_keywords:
- ICorDebugChain interface [.NET Framework debugging]
ms.assetid: f671f519-1cb3-4ae5-b9f1-abc5e783459f
topic_type:
- apiref
ms.openlocfilehash: 6ae0fec0f8de2bbe3862f9f70ed9cf3d32af34c4
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894207"
---
# <a name="icordebugchain-interface"></a>Interface ICorDebugChain

Representa um segmento de uma pilha de chamadas física ou lógica.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método EnumerateFrames](icordebugchain-enumerateframes-method.md)|Obtém um enumerador que contém todos os quadros de pilha gerenciados na cadeia, começando com o quadro mais recente.|  
|[Método GetActiveFrame](icordebugchain-getactiveframe-method.md)|Obtém o quadro ativo (ou seja, mais recente) na cadeia.|  
|[Método GetCallee](icordebugchain-getcallee-method.md)|Obtém a cadeia que foi chamada por essa cadeia.|  
|[Método GetCaller](icordebugchain-getcaller-method.md)|Obtém a cadeia que chamou essa cadeia.|  
|[Método GetContext](icordebugchain-getcontext-method.md)|Não implementado.|  
|[Método GetNext](icordebugchain-getnext-method.md)|Obtém a próxima cadeia de quadros para o thread.|  
|[Método GetPrevious](icordebugchain-getprevious-method.md)|Obtém a cadeia de quadros anterior para o thread.|  
|[Método GetReason](icordebugchain-getreason-method.md)|Obtém o motivo do Genesis desta cadeia de chamada.|  
|[Método GetRegisterSet](icordebugchain-getregisterset-method.md)|Obtém o conjunto de registros para a parte ativa desta cadeia.|  
|[Método GetStackRange](icordebugchain-getstackrange-method.md)|Obtém o intervalo de endereços do segmento da pilha para esta cadeia.|  
|[Método GetThread](icordebugchain-getthread-method.md)|Obtém o thread físico para o qual esta cadeia de chamadas faz parte.|  
|[Método IsManaged](icordebugchain-ismanaged-method.md)|Obtém um valor que indica se esta cadeia está executando código gerenciado.|  
  
## <a name="remarks"></a>Comentários  
 Os quadros de pilha em uma cadeia ocupam um espaço de pilha contíguo e compartilham o mesmo thread e contexto. Uma cadeia pode representar cadeias de código gerenciados ou não-gerenciadas. Uma instância `ICorDebugChain` vazia representa uma cadeia de código não gerenciada.  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](debugging-interfaces.md)
