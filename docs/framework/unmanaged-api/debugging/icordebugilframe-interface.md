---
title: Interface ICorDebugILFrame
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame
helpviewer_keywords:
- ICorDebugILFrame interface [.NET Framework debugging]
ms.assetid: d5cf5056-da4d-4629-914d-afe42a5393df
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a10c39d7df12c86b8fcf0fb40389c087f96e1ee
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965963"
---
# <a name="icordebugilframe-interface"></a>Interface ICorDebugILFrame

Representa um quadro de pilha do código Microsoft intermediate language (MSIL). Essa interface é uma subclasse da interface ICorDebugFrame.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CanSetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|Obtém um valor que indica se é seguro definir o ponteiro de instrução para o local de deslocamento especificado.|  
|[Método EnumerateArguments](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|Obtém um enumerador para os argumentos neste quadro.|  
|[Método EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|Obtém um enumerador para as variáveis locais neste quadro.|  
|[Método GetArgument](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|Obtém o valor do argumento especificado neste quadro de pilha MSIL.|  
|[Método GetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|Obtém o valor do ponteiro de instrução e um valor de combinação bit a bit que descreve como o valor do ponteiro de instrução foi obtido.|  
|[Método GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|Obtém o valor da variável local especificada neste quadro de pilha MSIL.|  
|[Método GetStackDepth](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|Não implementado.|  
|[Método GetStackValue](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|Não implementado.|  
|[Método SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|Define o ponteiro de instrução para o local de deslocamento especificado no código MSIL.|  
  
## <a name="remarks"></a>Comentários  
 O `ICorDebugILFrame` é uma interface ICorDebugFrame especializada. Ela é usada para quadros de código MSIL ou para just-in-time (JIT) compilados quadros. Os quadros compilado por JIT implementam ambos o `ICorDebugILFrame` interface e a interface ICorDebugNativeFrame.  
  
> [!NOTE]
>  Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
