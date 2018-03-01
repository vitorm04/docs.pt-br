---
title: ICorDebugChain Interface1
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6000f6d91b3fe2325868b9af58740e1c4cd76127
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchain-interface1"></a>ICorDebugChain Interface1
Representa um segmento de uma pilha de chamadas física ou lógica.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método EnumerateFrames](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-enumerateframes-method.md)|Obtém um enumerador que contém todos os quadros de pilha gerenciada na cadeia, começando com o quadro mais recente.|  
|[Método GetActiveFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getactiveframe-method.md)|Obtém o ativo (ou seja, mais recente) quadro da cadeia.|  
|[Método GetCallee](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcallee-method.md)|Obtém a cadeia que foi chamada por essa cadeia.|  
|[Método GetCaller](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcaller-method.md)|Obtém a cadeia que chamou essa cadeia.|  
|[Método GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcontext-method.md)|Não implementado.|  
|[Método GetNext](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getnext-method.md)|Obtém a próxima cadeia de quadros do thread.|  
|[Método GetPrevious](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getprevious-method.md)|Obtém a cadeia anterior de quadros do thread.|  
|[Método GetReason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)|Obtém o motivo para genesis dessa cadeia de chamada.|  
|[Método GetRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getregisterset-method.md)|Obtém o conjunto de registros de parte ativa dessa cadeia.|  
|[Método GetStackRange](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getstackrange-method.md)|Obtém o intervalo de endereços do segmento de pilha para essa cadeia.|  
|[Método GetThread](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getthread-method.md)|Obtém o segmento físico que essa cadeia de chamada é parte do.|  
|[Método IsManaged](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-ismanaged-method.md)|Obtém um valor que indica se esta cadeia está em execução de código gerenciado.|  
  
## <a name="remarks"></a>Comentários  
 Os quadros de pilha em uma cadeia ocupam espaço de pilha contíguas e compartilham o mesmo thread e o contexto. Uma cadeia pode representar ou cadeias de código gerenciado ou não gerenciado. Vazio `ICorDebugChain` instância representa uma cadeia de código não gerenciado.  
  
> [!NOTE]
>  Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
