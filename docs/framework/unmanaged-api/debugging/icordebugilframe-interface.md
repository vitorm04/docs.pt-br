---
title: ICorDebugILFrame Interface1
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1db53f50e942e70517fc06dfd90e75d04158ea9a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe-interface1"></a>ICorDebugILFrame Interface1
Representa um quadro de pilha do código Microsoft intermediate language (MSIL). Esta interface é uma subclasse da interface ICorDebugFrame.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CanSetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|Obtém um valor que indica se é seguro definir o ponteiro de instrução para o local de deslocamento especificado.|  
|[Método EnumerateArguments](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|Obtém um enumerador para os argumentos nesse quadro.|  
|[Método EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|Obtém um enumerador para as variáveis locais nesse quadro.|  
|[Método GetArgument](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|Obtém o valor do argumento especificado nesse quadro de pilha MSIL.|  
|[Método GetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|Obtém o valor do ponteiro de instrução e um valor de combinação bit a bit que descreve como o valor do ponteiro de instrução foi obtido.|  
|[Método GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|Obtém o valor da variável local especificada deste quadro de pilhas MSIL.|  
|[Método GetStackDepth](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|Não implementado.|  
|[Método GetStackValue](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|Não implementado.|  
|[Método SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|Define o ponteiro de instrução para o local de deslocamento especificado no código MSIL.|  
  
## <a name="remarks"></a>Comentários  
 O `ICorDebugILFrame` é uma interface ICorDebugFrame especializada. Ele é usado para os quadros de código MSIL ou just-in-time (JIT) compilados quadros. Os quadros de compilação JIT implementam o `ICorDebugILFrame` interface e a interface ICorDebugNativeFrame.  
  
> [!NOTE]
>  Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
