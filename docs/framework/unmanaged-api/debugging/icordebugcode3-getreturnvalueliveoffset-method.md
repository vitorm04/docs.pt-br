---
title: "Método ICorDebugCode3::GetReturnValueLiveOffset"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugCode3.GetReturnValueLiveOffset
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode3::GetReturnValueLiveOffset
helpviewer_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset method [.NET Framework debugging]
- GetReturnValueLiveOffset method [.NET Framework debugging]
ms.assetid: 8c2ff5d8-8c04-4423-b1e1-e1c8764b36d3
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5d10d298a031e7146eaf6cf7988538e6f7020136
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a>Método ICorDebugCode3::GetReturnValueLiveOffset
Para um deslocamento de IL especificado, obtém os deslocamentos nativo onde um ponto de interrupção deve ser colocado para que o depurador possa obter o valor de retorno de uma função.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,   
    [out] ULONG32 *pFetched,   
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ILoffset`  
 O deslocamento de IL. Ele deve ser um site de chamada de função ou a chamada de função falhará.  
  
 `bufferSize`  
 O número de bytes disponíveis para armazenar `pOffsets`.  
  
 `pFetched`  
 Um ponteiro para o número de deslocamentos de fato retornadas. Geralmente, seu valor é 1, mas uma única instrução IL pode mapear vários `CALL` instruções de assembly.  
  
 `pOffsets`  
 Uma matriz de deslocamentos nativo. Normalmente, `pOffsets` contém um desvio único, embora uma única instrução IL pode mapear para mapear vários para vários `CALL` instruções de assembly.  
  
## <a name="remarks"></a>Comentários  
 Esse método é usado junto com o [Icordebugilframe3](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) método para obter o valor de retorno de um método que retorna um tipo de referência. Passar um deslocamento para um site de chamada de função para este método de IL retorna um ou mais deslocamentos nativo. O depurador pode definir pontos de interrupção nesses deslocamentos nativo na função. Quando o depurador atingirá um dos pontos de interrupção, você pode passar o mesmo deslocamento de IL passado para este método para o [Icordebugilframe3](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) método para obter o valor de retorno. O depurador deve, em seguida, desmarque todos os pontos de interrupção que ele definiu.  
  
> [!WARNING]
>  O `ICorDebugCode3::GetReturnValueLiveOffset` e [Icordebugilframe3](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) métodos permitem que você obtenha informações do valor de retorno para somente tipos de referência. Recuperando informações de valor de retorno dos tipos de valor (ou seja, todos os tipos que derivam de <xref:System.ValueType>) não tem suporte.  
  
 A função retorna o `HRESULT` valores mostrados na tabela a seguir.  
  
|Valor `HRESULT`|Descrição|  
|---------------------|-----------------|  
|`S_OK`|Êxito.|  
|`CORDBG_E_INVALID_OPCODE`|No site de deslocamento de IL especificado não é uma instrução de chamada ou a função retornará `void`.|  
|`CORDBG_E_UNSUPPORTED`|O deslocamento de IL fornecido é uma chamada correta, mas o tipo de retorno não tem suporte para obter um valor de retorno.|  
  
 O `ICorDebugCode3::GetReturnValueLiveOffset` método está disponível apenas em baseados em x86 e sistemas AMD64.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)  
 [Interface ICorDebugCode3](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
