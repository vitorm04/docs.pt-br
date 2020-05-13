---
title: Interface ICorDebugNativeFrame
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
ms.openlocfilehash: dd87745a29514a2f9f05aa142baae4e05d4b4a7b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206598"
---
# <a name="icordebugnativeframe-interface"></a>Interface ICorDebugNativeFrame

Uma implementação especializada de ICorDebugFrame usada para quadros nativos.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CanSetIP](icordebugnativeframe-cansetip-method.md)|Obtém um valor que indica se é seguro definir o ponteiro de instrução para o local de deslocamento especificado no código nativo.|  
|[Método GetIP](icordebugnativeframe-getip-method.md)|Obtém o deslocamento do quadro de pilha no código nativo.|  
|[Método GetLocalDoubleRegisterValue](icordebugnativeframe-getlocaldoubleregistervalue-method.md)|Obtém um ponteiro para um ICorDebugValue que representa o valor de um argumento ou variável local armazenado em dois registros de memória de um quadro nativo.|  
|[Método GetLocalMemoryRegisterValue](icordebugnativeframe-getlocalmemoryregistervalue-method.md)|Obtém um ponteiro para um `ICorDebugValue` que representa o valor de uma variável local, da qual os bits baixos são armazenados no registro especificado e os bits altos são armazenados no endereço de memória especificado.|  
|[Método GetLocalMemoryValue](icordebugnativeframe-getlocalmemoryvalue-method.md)|Obtém um ponteiro para um `ICorDebugValue` que representa o valor de uma variável local armazenada no endereço de memória especificado.|  
|[Método GetLocalRegisterMemoryValue](icordebugnativeframe-getlocalregistermemoryvalue-method.md)|Obtém um ponteiro para um `ICorDebugValue` que representa o valor de uma variável local, da qual os bits altos são armazenados no registro especificado e os bits baixos são armazenados no endereço de memória especificado|  
|[Método GetLocalRegisterValue](icordebugnativeframe-getlocalregistervalue-method.md)|Obtém um ponteiro para um `ICorDebugValue` que representa o valor de um argumento ou uma variável local armazenada no registro nativo especificado.|  
|[Método GetRegisterSet](icordebugnativeframe-getregisterset-method.md)|Obtém um ponteiro para um [ICorDebugRegisterSet](icordebugregisterset-interface.md) que representa o conjunto de registros para isso `ICorDebugNativeFrame` .|  
|[Método SetIP](icordebugnativeframe-setip-method.md)|Define o ponteiro de instrução para o local de deslocamento especificado no código nativo.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Depurando interfaces](debugging-interfaces.md)
