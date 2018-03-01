---
title: ICorDebugAssembly Interface1
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
- ICorDebugAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly
helpviewer_keywords:
- ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 9d657a28-6984-4c5e-8a54-89d20080baff
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6331c00c2be0805afb56028e9e1a13cd11168cf1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugassembly-interface1"></a>ICorDebugAssembly Interface1
Representa um assembly.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método EnumerateModules](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)|Obtém um enumerador para os módulos contidos no assembly.|  
|[Método GetAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getappdomain-method.md)|Obtém um ponteiro de interface para o domínio de aplicativo que contém essa `ICorDebugAssembly` instância.|  
|[Método GetCodeBase](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getcodebase-method.md)|Não implementado na versão atual do .NET Framework.|  
|[Método GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getname-method.md)|Obtém o nome do assembly.|  
|[Método GetProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getprocess-method.md)|Obtém a instância de ICorDebugProcess no qual o assembly está em execução.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
