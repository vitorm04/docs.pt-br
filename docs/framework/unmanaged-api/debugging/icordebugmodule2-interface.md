---
title: Interface1 ICorDebugModule2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule2
helpviewer_keywords: ICorDebugModule2 interface [.NET Framework debugging]
ms.assetid: 0847e64f-fdbe-4c96-8168-da20fdc84d80
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 97259783d34babe3f0f229f5d62b3e945c0ac624
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodule2-interface1"></a>Interface1 ICorDebugModule2
Serve como uma extensão lógica para a interface ICorDebugModule.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)|Aplica as alterações nos metadados e as alterações no código Microsoft intermediate language (MSIL) para o processo em execução.|  
|[Método GetJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-getjitcompilerflags-method.md)|Obtém os sinalizadores que controlam a compilação just-in-time (JIT) para este `ICorDebugModule2`.|  
|[Método ResolveAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-resolveassembly-method.md)|Resolve o assembly referenciado pelo token de metadados especificado.|  
|[Método SetJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)|Define os sinalizadores que controlam a compilação JIT para este `ICorDebugModule2`.|  
|[Método SetJMCStatus](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjmcstatus-method.md)|Define o status de apenas meu código (JMC) de todos os métodos de todas as classes neste `ICorDebugModule2` para o valor especificado, exceto aqueles na `pTokens` matriz, que define como o valor oposto.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
