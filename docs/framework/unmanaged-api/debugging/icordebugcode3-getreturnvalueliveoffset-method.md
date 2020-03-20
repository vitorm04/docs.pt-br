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
ms.openlocfilehash: 34d543dd76de05bdf55d8187cf192455d1387a9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178947"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a>Método ICorDebugCode3::GetReturnValueLiveOffset
Para uma compensação IL especificada, obtém as compensações nativas onde um ponto de ruptura deve ser colocado para que o depurador possa obter o valor de retorno de uma função.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,
    [out] ULONG32 *pFetched,
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `ILoffset`  
 O deslocamento do IL. Deve ser um local de chamada de função ou a chamada da função falhará.  
  
 `bufferSize`  
 O número de bytes `pOffsets`disponíveis para armazenar .  
  
 `pFetched`  
 Um ponteiro para o número de deslocamentos realmente retornou. Normalmente, seu valor é 1, mas uma `CALL` única instrução il pode mapear para várias instruções de montagem.  
  
 `pOffsets`  
 Uma série de deslocamentos nativos. Normalmente, `pOffsets` contém um único deslocamento, embora uma única instrução il possa mapear para vários mapas para várias `CALL` instruções de montagem.  
  
## <a name="remarks"></a>Comentários  
 Este método é usado juntamente com o método [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) para obter o valor de retorno de um método que retorna um tipo de referência. Passar um deslocamento de IL para um local de chamada de função para este método retorna um ou mais deslocamentos nativos. O depurador pode, então, definir pontos de interrupção nesses deslocamentos nativos na função. Quando o depurador atinge um dos pontos de interrupção, você pode passar o mesmo deslocamento de IL que você passou para este método para o método [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) para obter o valor de retorno. O depurador deve então limpar todos os pontos de interrupção que ele definiu.  
  
> [!WARNING]
> Os `ICorDebugCode3::GetReturnValueLiveOffset` métodos [ICorDebugILFrame3:GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) permitem que você obtenha informações de valor de retorno apenas para tipos de referência. A recuperação de informações de valor de retorno de <xref:System.ValueType>tipos de valor (ou seja, todos os tipos que derivam ) não é suportada.  
  
 A função `HRESULT` retorna os valores mostrados na tabela a seguir.  
  
|`HRESULT` valor|Descrição|  
|---------------------|-----------------|  
|`S_OK`|Sucesso.|  
|`CORDBG_E_INVALID_OPCODE`|O site de deslocamento il dado não `void`é uma instrução de chamada, ou a função retorna .|  
|`CORDBG_E_UNSUPPORTED`|O deslocamento de IL dado é uma chamada adequada, mas o tipo de retorno não é suportado para obter um valor de retorno.|  
  
 O `ICorDebugCode3::GetReturnValueLiveOffset` método está disponível apenas nos sistemas x86 e AMD64.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Método GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md)
- [Interface ICorDebugCode3](icordebugcode3-interface.md)
