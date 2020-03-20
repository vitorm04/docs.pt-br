---
title: Método ICorDebugILFrame3::GetReturnValueForILOffset
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
api_name:
- ICorDebugILFrame3.GetReturnValueForILOffset
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 06522727-5f64-4391-9331-11386883c352
topic_type:
- apiref
ms.openlocfilehash: 0d1ef6c1369fd399f5b36b24a21c4b5d7f1e80fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178808"
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a>Método ICorDebugILFrame3::GetReturnValueForILOffset
Obtém um objeto "ICorDebugValue" que encapsula o valor de retorno de uma função.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `ILOffset`  
 O deslocamento do IL. Consulte a seção Comentários.  
  
 `ppReturnValue`  
 Um ponteiro para o endereço de um objeto de interface "ICorDebugValue" que fornece informações sobre o valor de retorno de uma chamada de função.  
  
## <a name="remarks"></a>Comentários  
 Este método é usado juntamente com o método [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) para obter o valor de retorno de um método. É particularmente útil no caso de métodos cujos valores de retorno são ignorados, como nos dois exemplos de código a seguir. O primeiro exemplo <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> chama o método, mas ignora o valor de retorno do método.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 O segundo exemplo ilustra um problema muito mais comum na depuração. Como um método é usado como argumento em uma chamada de método, seu valor de retorno só é acessível quando o depurador passa pelo método chamado. Em muitos casos, particularmente quando o chamado método é definido em uma biblioteca externa, isso não é possível.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 Se você passar pelo [método ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) um deslocamento il para um site de chamada de função, ele retorna um ou mais deslocamentos nativos. O depurador pode, então, definir pontos de interrupção nesses deslocamentos nativos na função. Quando o depurador atinge um dos pontos de interrupção, você pode então passar o mesmo deslocamento il que você passou para este método para obter o valor de retorno. O depurador deve então limpar todos os pontos de interrupção que ele definiu.  
  
> [!WARNING]
> O Método e métodos [ICorDebugCode3:GetReturnValueLiveOffset Method](icordebugcode3-getreturnvalueliveoffset-method.md) e `ICorDebugILFrame3::GetReturnValueForILOffset` os métodos permitem obter informações de valor de retorno apenas para tipos de referência. A recuperação de informações de valor de retorno de <xref:System.ValueType>tipos de valor (ou seja, todos os tipos que derivam ) não é suportada.  
  
 O deslocamento DE IL `ILOffset` especificado pelo parâmetro deve estar em um local de chamada de função, e a depuração deve ser interrompida em um ponto de ruptura definido no deslocamento nativo retornado pelo método [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) para o mesmo deslocamento de IL. Se a depuração não for interrompida no local correto para a compensação IL especificada, a API falhará.  
  
 Se a chamada de função não retornar um valor, a API falhará.  
  
 O `ICorDebugILFrame3::GetReturnValueForILOffset` método está disponível apenas nos sistemas x86 e AMD64.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Método GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md)
- [Interface ICorDebugILFrame3](icordebugilframe3-interface.md)
