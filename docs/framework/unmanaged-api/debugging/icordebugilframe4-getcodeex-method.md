---
title: ICorDebugILFrame4::Método GetCodeEx
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetLocalVariableEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aeda0e42-29ee-4ca8-9f21-ac4641677a62
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb50459e36cfeb76a0c9a1e1cd4544260d484f45
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926791"
---
# <a name="icordebugilframe4getcodeex-method"></a>ICorDebugILFrame4::Método GetCodeEx
[Com suporte no .NET Framework 4.5.2 e versões posteriores]  
  
 Obtém um ponteiro para o código que este registro de ativação está executando.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `flags`  
 no Um membro de enumeração [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) que especifica se a Il (linguagem intermediária) definida pela solicitação ReJIT do criador de perfil está incluída no quadro.  
  
 `ppCode`  
 fora Um ponteiro para o endereço de um objeto "ICorDebugCode" que representa o código que esse quadro de pilha está executando.  
  
## <a name="remarks"></a>Comentários  
 Esse método é semelhante ao método [ICorDebugFrame:: GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) , exceto pelo fato de que ele acessa opcionalmente o código definido pela solicitação ReJIT do criador de perfil. Chamar esse método com um `flags` valor de `ILCODE_ORIGINAL_IL` é equivalente a chamar [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); se o método for instrumentado, seu Il não estará acessível. `ILCODE_REJIT_IL` permite que o depurador acesse a IL definida pela solicitação ReJIT do criador de perfil. Se o Il não for instrumentado, `ppCode` será **NULL**e o método retornará. `S_OK`  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugILFrame4](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [ReJIT: Um guia de instruções](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
