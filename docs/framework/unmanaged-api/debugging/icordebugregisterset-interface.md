---
title: Interface ICorDebugRegisterSet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet
helpviewer_keywords: ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: d3d9676d-0b87-4bc3-b679-7bbc7a186c88
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0ccff205758dee2ffc6a6432ab20b3310147eb06
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugregisterset-interface"></a>Interface ICorDebugRegisterSet
Representa o conjunto de registros disponíveis no computador que está executando o código.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetRegisters](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)|Obtém o valor de cada registro (no computador que está executando código) que é especificado pela máscara de bits.|  
|[Método GetRegistersAvailable](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md)|Obtém um pouco máscara indicando que registra neste `ICorDebugRegisterSet` estão disponíveis no momento.|  
|[Método GetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getthreadcontext-method.md)|Obtém o contexto do thread atual.|  
|[Método SetRegisters](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setregisters-method.md)|Não implementado para o .NET Framework versão 2.0.|  
|[Método SetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setthreadcontext-method.md)|Não implementado para o .NET Framework 2.0.|  
  
## <a name="remarks"></a>Comentários  
 O `ICorDebugRegisterSet` interface oferece suporte a registros somente 32 bits. Use o [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) interface em plataformas, como IA-64 que exigem registros adicionais.  
  
> [!NOTE]
>  Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Interface ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
