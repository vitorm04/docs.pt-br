---
title: Interface ICorDebugThread4
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread4
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread4
helpviewer_keywords: ICorDebugThread4 interface [.NET Framework debugging]
ms.assetid: a8c7719a-322b-4133-8566-4c27218dc104
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e54611a38193a05a33381e798a61977d7aec41a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugthread4-interface"></a>Interface ICorDebugThread4
Fornece informações de bloqueio de thread.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetBlockingObjects](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getblockingobjects-method.md)|Fornece uma enumeração ordenada de [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) estruturas que fornecem informações de bloqueio de thread.|  
|[Método HadUnhandledException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-hadunhandledexception-method.md)|Indica se o thread nunca teve uma exceção sem tratamento.|  
|[Método GetCurrentCustomDebuggerNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md)|Obtém a atual [Icordebugmanagedcallback3](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) objeto no thread atual.|  
  
## <a name="remarks"></a>Comentários  
 Esta interface é uma extensão de lógica de ICorDebugThread, ICorDebugThread2, e [ICorDebugThread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md) interfaces.  
  
> [!NOTE]
>  Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
