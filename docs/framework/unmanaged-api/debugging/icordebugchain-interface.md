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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01dded47fca26df11781153eb45693057a25ad01
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220702"
---
# <a name="icordebugchain-interface"></a>Interface ICorDebugChain

Representa um segmento de uma pilha de chamadas física ou lógica.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método EnumerateFrames](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-enumerateframes-method.md)|Obtém um enumerador que contém todos os quadros de pilha gerenciada na cadeia, começando com o quadro mais recente.|  
|[Método GetActiveFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getactiveframe-method.md)|Obtém o ativo (ou seja, mais recente) quadro da cadeia.|  
|[Método GetCallee](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcallee-method.md)|Obtém a cadeia que foi chamada por essa cadeia.|  
|[Método GetCaller](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcaller-method.md)|Obtém a cadeia que chamou esta cadeia.|  
|[Método GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcontext-method.md)|Não implementado.|  
|[Método GetNext](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getnext-method.md)|Obtém a próxima cadeia de quadros do thread.|  
|[Método GetPrevious](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getprevious-method.md)|Obtém a cadeia anterior de quadros do thread.|  
|[Método GetReason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)|Obtém o motivo para a gênese dessa cadeia de chamada.|  
|[Método GetRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getregisterset-method.md)|Obtém o conjunto de registros de parte ativa dessa cadeia.|  
|[Método GetStackRange](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getstackrange-method.md)|Obtém o intervalo de endereços do segmento de pilha para essa cadeia.|  
|[Método GetThread](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getthread-method.md)|Obtém o thread físico que essa cadeia de chamada é parte do.|  
|[Método IsManaged](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-ismanaged-method.md)|Obtém um valor que indica se esta cadeia está em execução de código gerenciado.|  
  
## <a name="remarks"></a>Comentários  
 Os quadros de pilha em uma cadeia ocupam espaço na pilha contíguos e compartilham o mesmo thread e contexto. Uma cadeia pode representar qualquer cadeias de código gerenciado ou não gerenciado. Vazio `ICorDebugChain` instância representa uma cadeia de código não gerenciado.  
  
> [!NOTE]
>  Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
