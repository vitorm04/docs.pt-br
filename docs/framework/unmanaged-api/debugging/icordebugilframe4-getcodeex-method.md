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
ms.openlocfilehash: ef2e4bc0caddd6b13c8dbe8edb59e0673519421b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178788"
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
  
## <a name="parameters"></a>parâmetros  
 `flags`  
 [em] Um membro de enumeração [ILCodeKind](ilcodekind-enumeration.md) que especifica se o idioma intermediário (IL) definido pela solicitação ReJIT do profiler está incluído no quadro.  
  
 `ppCode`  
 [fora] Um ponteiro para o endereço de um objeto "ICorDebugCode" que representa o código que este quadro de pilha está executando.  
  
## <a name="remarks"></a>Comentários  
 Este método é semelhante ao método [ICorDebugFrame::GetCode,](icordebugframe-getcode-method.md) exceto que ele acessa opcionalmente o código definido pela solicitação ReJIT do profiler. Chamar este método `flags` com `ILCODE_ORIGINAL_IL` um valor de é equivalente a chamar [GetCode;](icordebugframe-getcode-method.md) se o método for instrumentado, seu IL não será acessível. `ILCODE_REJIT_IL` permite que o depurador acesse a IL definida pela solicitação ReJIT do criador de perfil. Se o IL não `ppCode` for instrumentado, `S_OK`será **nulo**e o método retornar.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebugILFrame4](icordebugilframe4-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
- [ReJIT: Um Guia de Como Fazer](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
