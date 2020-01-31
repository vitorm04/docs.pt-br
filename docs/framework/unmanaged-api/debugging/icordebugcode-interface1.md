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
ms.openlocfilehash: 4b24b3dfe6a931866acd7eba966811071ff39ea5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788934"
---
# <a name="icordebugcode-interface"></a>Interface ICorDebugCode

Representa um segmento de código MSIL (Microsoft Intermediate Language) ou código nativo.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CreateBreakpoint](icordebugcode-createbreakpoint-method.md)|Cria um ponto de interrupção no deslocamento especificado.|  
|[Método GetAddress](icordebugcode-getaddress-method.md)|Obtém o endereço virtual relativo (RVA) do segmento de código que este `ICorDebugCode` representa.|  
|[Método GetCode](icordebugcode-getcode-method.md)|Obtém todo o código para a função especificada, formatado para desmontagem. Esse método foi preterido; Use [ICorDebugCode2:: GetCodeChunks](icordebugcode2-getcodechunks-method.md) em vez disso.|  
|[Método GetEnCRemapSequencePoints](icordebugcode-getencremapsequencepoints-method.md)|Não implementado.|  
|[Método GetFunction](icordebugcode-getfunction-method.md)|Obtém o "ICorDebugFunction" associado a este `ICorDebugCode`.|  
|[Método GetILToNativeMapping](icordebugcode-getiltonativemapping-method.md)|Obtém uma matriz de instâncias "COR_DEBUG_IL_TO_NATIVE_MAP" que representam mapeamentos de deslocamentos MSIL para deslocamentos nativos.|  
|[Método GetSize](icordebugcode-getsize-method.md)|Obtém o tamanho, em bytes, do código binário representado por essa `ICorDebugCode`.|  
|[Método GetVersionNumber](icordebugcode-getversionnumber-method.md)|Obtém o número baseado em um que identifica a versão do código que esse `ICorDebugCode` representa.|  
|[Método IsIL](icordebugcode-isil-method.md)|Obtém um valor que indica se este `ICorDebugCode` é compilado em MSIL.|  
  
## <a name="remarks"></a>Comentários  
 `ICorDebugCode` pode representar o MSIL ou código nativo. Um objeto "ICorDebugFunction" que representa o código MSIL pode ter zero ou um `ICorDebugCode` objetos associados a ele. Um objeto "ICorDebugFunction" que representa o código nativo pode ter qualquer número de objetos `ICorDebugCode` associados a ele.  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugCode3](icordebugcode3-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
