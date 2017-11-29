---
title: Interface ICorDebugFunction3
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction3
api_location: mscordbi.dll
api_type: COM
ms.assetid: b22717b9-ead5-4eea-887e-789b52d613dc
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cfe0c420c1c9b8074b7cb769e592f8cb2f5916e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugfunction3-interface"></a>Interface ICorDebugFunction3
[Com suporte no .NET Framework 4.5.2 e versões posteriores]  
  
 Logicamente estende a interface ICorDebugFunction para fornecer acesso ao código de uma solicitação ReJIT.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetActiveReJitRequestILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)|Obtém um ponteiro de interface para um [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) que contém o IL de uma solicitação ReJIT ativa.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)  
 [ReJIT: Um guia de instruções](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
