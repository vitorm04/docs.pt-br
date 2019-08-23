---
title: Interface ICorDebugCode
ms.date: 03/30/2017
api_name:
- ICorDebugCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode
helpviewer_keywords:
- ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7bd14fb6-8b54-4484-a891-e3c21859c019
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75cc8ea9d88dda42362f50b519864b1a78e1a64b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960789"
---
# <a name="icordebugcode-interface"></a>Interface ICorDebugCode

Representa um segmento de código MSIL (Microsoft Intermediate Language) ou código nativo.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CreateBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-createbreakpoint-method.md)|Cria um ponto de interrupção no deslocamento especificado.|  
|[Método GetAddress](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getaddress-method.md)|Obtém o endereço virtual relativo (RVA) do segmento de código que isso `ICorDebugCode` representa.|  
|[Método GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)|Obtém todo o código para a função especificada, formatado para desmontagem. Esse método foi preterido; Use [ICorDebugCode2:: GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) em vez disso.|  
|[Método GetEnCRemapSequencePoints](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getencremapsequencepoints-method.md)|Não implementado.|  
|[Método GetFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getfunction-method.md)|Obtém o "ICorDebugFunction" associado a isso `ICorDebugCode`.|  
|[Método GetILToNativeMapping](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)|Obtém uma matriz de instâncias "COR_DEBUG_IL_TO_NATIVE_MAP" que representam mapeamentos de deslocamentos MSIL para deslocamentos nativos.|  
|[Método GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getsize-method.md)|Obtém o tamanho, em bytes, do código binário representado por isso `ICorDebugCode`.|  
|[Método GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)|Obtém o número baseado em um que identifica a versão do código que `ICorDebugCode` representa.|  
|[Método IsIL](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-isil-method.md)|Obtém um valor que indica se isso `ICorDebugCode` é compilado em MSIL.|  
  
## <a name="remarks"></a>Comentários  
 `ICorDebugCode`pode representar o MSIL ou código nativo. Um objeto "ICorDebugFunction" que representa o código MSIL pode ter zero ou um `ICorDebugCode` objetos associados a ele. Um objeto "ICorDebugFunction" que representa o código nativo pode ter qualquer número `ICorDebugCode` de objetos associados a ele.  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugCode3](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
