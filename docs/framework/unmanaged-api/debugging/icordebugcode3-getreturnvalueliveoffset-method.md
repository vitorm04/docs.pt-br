---
title: Método ICorDebugCode3::GetReturnValueLiveOffset
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugCode3.GetReturnValueLiveOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset
helpviewer_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset method [.NET Framework debugging]
- GetReturnValueLiveOffset method [.NET Framework debugging]
ms.assetid: 8c2ff5d8-8c04-4423-b1e1-e1c8764b36d3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03ee275336d3ae71f63d82add694fe1308efbe8b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125925"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a>Método ICorDebugCode3::GetReturnValueLiveOffset
Para um deslocamento especificado do IL, obtém os deslocamentos nativos onde um ponto de interrupção deve ser colocado para que o depurador possa obter o valor de retorno de uma função.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,   
    [out] ULONG32 *pFetched,   
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ILoffset`  
 O deslocamento de IL. Ele deve ser um site de chamada de função ou a chamada de função falhará.  
  
 `bufferSize`  
 O número de bytes disponíveis para armazenar `pOffsets`.  
  
 `pFetched`  
 Um ponteiro para o número de deslocamentos que realmente retornada. Geralmente, seu valor é 1, mas uma única declaração IL pode mapear para várias `CALL` instruções de assembly.  
  
 `pOffsets`  
 Uma matriz de deslocamentos nativos. Normalmente, `pOffsets` contém um único deslocamento, embora uma única declaração IL pode mapear para vários mapas para várias `CALL` instruções de assembly.  
  
## <a name="remarks"></a>Comentários  
 Esse método é usado junto com o [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) método para obter o valor de retorno de um método que retorna um tipo de referência. Passar um deslocamento do IL para um site de chamada de função para esse método retorna um ou mais deslocamentos nativos. O depurador pode, em seguida, definir pontos de interrupção nesses deslocamentos nativos na função. Quando o depurador encontra um dos pontos de interrupção, você pode passar o mesmo IL de deslocamento que passou para este método para o [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) método para obter o valor de retorno. O depurador deve desmarcar todos os pontos de interrupção definido por ele.  
  
> [!WARNING]
>  O `ICorDebugCode3::GetReturnValueLiveOffset` e [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) métodos permitem que você obtenha informações de valor de retorno para tipos de referência apenas. Recuperando informações de valor de retorno de tipos de valor (ou seja, todos os tipos que derivam de <xref:System.ValueType>) não tem suporte.  
  
 A função retorna o `HRESULT` valores mostrados na tabela a seguir.  
  
|Valor `HRESULT`|Descrição|  
|---------------------|-----------------|  
|`S_OK`|Êxito.|  
|`CORDBG_E_INVALID_OPCODE`|O site de deslocamento IL determinado não é uma instrução de chamada ou a função retornará `void`.|  
|`CORDBG_E_UNSUPPORTED`|O deslocamento IL determinado é uma chamada apropriada, mas o tipo de retorno tem suporte para obter um valor de retorno.|  
  
 O `ICorDebugCode3::GetReturnValueLiveOffset` método está disponível apenas em baseados em x86 e AMD64 sistemas.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Método GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)
- [Interface ICorDebugCode3](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
