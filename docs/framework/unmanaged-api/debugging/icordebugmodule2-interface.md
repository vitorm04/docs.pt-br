---
title: Interface ICorDebugModule2
ms.date: 03/30/2017
api_name:
- ICorDebugModule2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2
helpviewer_keywords:
- ICorDebugModule2 interface [.NET Framework debugging]
ms.assetid: 0847e64f-fdbe-4c96-8168-da20fdc84d80
topic_type:
- apiref
ms.openlocfilehash: 32774aacecf3e56510bc6f0670538a44fde794c9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792984"
---
# <a name="icordebugmodule2-interface"></a>Interface ICorDebugModule2

Serve como uma extensão lógica para a interface ICorDebugModule.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método ApplyChanges](icordebugmodule2-applychanges-method.md)|Aplica as alterações nos metadados e as alterações no código MSIL (Microsoft Intermediate Language) para o processo em execução.|  
|[Método GetJITCompilerFlags](icordebugmodule2-getjitcompilerflags-method.md)|Obtém os sinalizadores que controlam a compilação JIT (just-in-time) para este `ICorDebugModule2`.|  
|[Método ResolveAssembly](icordebugmodule2-resolveassembly-method.md)|Resolve o assembly referenciado pelo token de metadados especificado.|  
|[Método SetJITCompilerFlags](icordebugmodule2-setjitcompilerflags-method.md)|Define os sinalizadores que controlam a compilação JIT para este `ICorDebugModule2`.|  
|[Método SetJMCStatus](icordebugmodule2-setjmcstatus-method.md)|Define o status de Apenas Meu Código (JMC) de todos os métodos de todas as classes neste `ICorDebugModule2` para o valor especificado, exceto aqueles na matriz de `pTokens`, que ele define para o valor oposto.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
