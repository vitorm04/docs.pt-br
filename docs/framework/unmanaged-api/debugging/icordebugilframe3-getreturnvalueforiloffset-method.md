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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 315bd78f660e093ecbf65224bd09a9b4f44300b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420928"
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a>Método ICorDebugILFrame3::GetReturnValueForILOffset
Obtém um objeto de "ICorDebugValue" que encapsula o valor de retorno de uma função.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,   
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ILOffset`  
 O deslocamento de IL. Consulte a seção Comentários.  
  
 `ppReturnValue`  
 Um ponteiro para o endereço de um objeto de interface de "ICorDebugValue" que fornece informações sobre o valor de retorno de uma chamada de função.  
  
## <a name="remarks"></a>Comentários  
 Esse método é usado junto com o [Icordebugcode3](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) método para obter o valor de retorno de um método. Isso é especialmente útil no caso de métodos cujos valores de retorno são ignorados, como os seguir dois exemplos de código. O primeiro exemplo chama o <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> método, mas ignora o valor de retorno do método.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 O segundo exemplo ilustra um problema muito mais comuns na depuração. Como um método é usado como um argumento em uma chamada de método, o valor de retorno é acessível somente quando o depurador percorre o método chamado. Em muitos casos, especialmente quando o método chamado é definido em uma biblioteca externa, que não é possível.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 Se você passar o [Icordebugcode3](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) método um deslocamento para um site de chamada de função de IL, retorna um ou mais deslocamentos nativo. O depurador pode definir pontos de interrupção nesses deslocamentos nativo na função. Quando o depurador atingirá um dos pontos de interrupção, você pode passar o mesmo deslocamento de IL passado para este método para obter o valor de retorno. O depurador deve, em seguida, desmarque todos os pontos de interrupção que ele definiu.  
  
> [!WARNING]
>  O [método Icordebugcode3](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) e `ICorDebugILFrame3::GetReturnValueForILOffset` métodos permitem que você obtenha informações do valor de retorno para somente tipos de referência. Recuperando informações de valor de retorno dos tipos de valor (ou seja, todos os tipos que derivam de <xref:System.ValueType>) não tem suporte.  
  
 O deslocamento de IL especificado pelo `ILOffset` parâmetro deve estar em um site de chamada de função e o depurador deve ser interrompido em um ponto de interrupção definido no deslocamento nativo retornado pelo [Icordebugcode3](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) método para o mesmo deslocamento de IL. Se o depurador não está parado no local correto para o deslocamento de IL especificado, a API falhará.  
  
 Se a chamada de função não retorna um valor, a API falhará.  
  
 O `ICorDebugILFrame3::GetReturnValueForILOffset` método está disponível apenas em baseados em x86 e sistemas AMD64.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)  
 [Interface ICorDebugILFrame3](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
