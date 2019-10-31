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
ms.openlocfilehash: c7419e5c3677b5679a0ca5c234463ae6e205b7d1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090371"
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
  
## <a name="parameters"></a>Parâmetros  
 `ILOffset`  
 O deslocamento de IL. Consulte a seção Comentários.  
  
 `ppReturnValue`  
 Um ponteiro para o endereço de um objeto de interface "ICorDebugValue" que fornece informações sobre o valor de retorno de uma chamada de função.  
  
## <a name="remarks"></a>Comentários  
 Esse método é usado junto com o método [ICorDebugCode3:: GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) para obter o valor de retorno de um método. Ele é particularmente útil no caso de métodos cujos valores de retorno são ignorados, como nos dois exemplos de código a seguir. O primeiro exemplo chama o método <xref:System.Int32.TryParse%2A?displayProperty=nameWithType>, mas ignora o valor de retorno do método.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 O segundo exemplo ilustra um problema muito mais comum na depuração. Como um método é usado como um argumento em uma chamada de método, seu valor de retorno é acessível somente quando o depurador percorre o método chamado. Em muitos casos, particularmente quando o método chamado é definido em uma biblioteca externa, isso não é possível.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 Se você passar o método [ICorDebugCode3:: GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) de um deslocamento IL para um site de chamada de função, ele retornará um ou mais deslocamentos nativos. O depurador pode então definir pontos de interrupção nesses deslocamentos nativos na função. Quando o depurador atinge um dos pontos de interrupção, você pode passar o mesmo deslocamento de IL passado para esse método para obter o valor de retorno. O depurador deve limpar todos os pontos de interrupção definidos por ele.  
  
> [!WARNING]
> O [método ICorDebugCode3:: GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) e os métodos `ICorDebugILFrame3::GetReturnValueForILOffset` permitem que você obtenha informações de valor de retorno somente para tipos de referência. Não há suporte para a recuperação de informações de valor de retorno de tipos de valor (ou seja, todos os tipos que derivam de <xref:System.ValueType>).  
  
 O deslocamento de IL especificado pelo parâmetro `ILOffset` deve estar em um site de chamada de função e o depurado deve ser interrompido em um ponto de interrupção definido no deslocamento nativo retornado pelo método [ICorDebugCode3:: GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) para o mesmo deslocamento de Il. Se o depurador não for interrompido no local correto para o deslocamento IL especificado, a API falhará.  
  
 Se a chamada de função não retornar um valor, a API falhará.  
  
 O método `ICorDebugILFrame3::GetReturnValueForILOffset` só está disponível em sistemas baseados em x86 e AMD64.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Método GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)
- [Interface ICorDebugILFrame3](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
