---
title: ICorDebugNativeFrame Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame
helpviewer_keywords:
- ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 04819c58-7246-4b32-befb-680cf1dbc436
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7996d5800e99d8e6161e24f34604aff3e4e906bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421997"
---
# <a name="icordebugnativeframe-interface1"></a>ICorDebugNativeFrame Interface1
Uma implementação especializada de ICorDebugFrame usado para quadros nativos.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CanSetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-cansetip-method.md)|Obtém um valor que indica se é seguro definir o ponteiro de instrução para o local de deslocamento especificado em código nativo.|  
|[Método GetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getip-method.md)|Obtém o deslocamento do quadro de pilha em código nativo.|  
|[Método GetLocalDoubleRegisterValue](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocaldoubleregistervalue-method.md)|Obtém um ponteiro para um ICorDebugValue que representa o valor de um argumento ou uma variável local armazenados em dois registros de memória de um quadro nativo.|  
|[Método GetLocalMemoryRegisterValue](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryregistervalue-method.md)|Obtém um ponteiro para um `ICorDebugValue` que representa o valor de uma variável local, dos quais os bits baixos são armazenados no registro especificado e os bits altos são armazenados no endereço de memória especificado.|  
|[Método GetLocalMemoryValue](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryvalue-method.md)|Obtém um ponteiro para um `ICorDebugValue` que representa o valor de uma variável local armazenado no endereço de memória especificado.|  
|[Método GetLocalRegisterMemoryValue](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistermemoryvalue-method.md)|Obtém um ponteiro para um `ICorDebugValue` que representa o valor de uma variável local, dos quais os bits altos são armazenados no registro especificado e os bits baixos são armazenados no endereço de memória especificado|  
|[Método GetLocalRegisterValue](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistervalue-method.md)|Obtém um ponteiro para um `ICorDebugValue` que representa o valor de um argumento ou uma variável local armazenado no registro nativo especificado.|  
|[Método GetRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getregisterset-method.md)|Obtém um ponteiro para um [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) que representa o conjunto de registros de isso `ICorDebugNativeFrame`.|  
|[Método SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)|Define o ponteiro de instrução para o local de deslocamento especificado em código nativo.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
