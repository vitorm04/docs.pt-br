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
ms.openlocfilehash: 9ca47eb5508907297a78dba1ab2b0a6d2b8ece0d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750235"
---
# <a name="icordebugcode-interface"></a>Interface ICorDebugCode

Representa um segmento de código MSIL (Microsoft Intermediate Language) ou código nativo.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CreateBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-createbreakpoint-method.md)|Cria um ponto de interrupção no deslocamento especificado.|  
|[Método GetAddress](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getaddress-method.md)|Obtém o endereço virtual relativo (RVA) do segmento de código que isso `ICorDebugCode` representa.|  
|[Método GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)|Obtém todo o código para a função especificada, formatada para desmontagem. Esse método foi preterido; Use [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) em vez disso.|  
|[Método GetEnCRemapSequencePoints](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getencremapsequencepoints-method.md)|Não implementado.|  
|[Método GetFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getfunction-method.md)|Obtém o "ICorDebugFunction" associado a este `ICorDebugCode`.|  
|[Método GetILToNativeMapping](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)|Obtém uma matriz de instâncias de "COR_DEBUG_IL_TO_NATIVE_MAP" que representam os mapeamentos de deslocamentos do MSIL para deslocamentos nativos.|  
|[Método GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getsize-method.md)|Obtém o tamanho, em bytes, do código binário representado por este `ICorDebugCode`.|  
|[Método GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)|Obtém o baseado em um número que identifica a versão do código que este `ICorDebugCode` representa.|  
|[Método IsIL](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-isil-method.md)|Obtém um valor que indica se este `ICorDebugCode` é compilada no MSIL.|  
  
## <a name="remarks"></a>Comentários  
 `ICorDebugCode` pode representar MSIL ou código nativo. Um objeto de "ICorDebugFunction" que representa o código MSIL pode ter zero ou um `ICorDebugCode` objetos associados a ele. Um objeto de "ICorDebugFunction" que representa o código nativo pode ter qualquer número de `ICorDebugCode` objetos associados a ele.  
  
> [!NOTE]
>  Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugCode3](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
