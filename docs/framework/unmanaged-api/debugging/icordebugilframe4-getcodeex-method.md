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
ms.openlocfilehash: 24be4507e8ad6cde1e9c50582e352f0fc9b12ed3
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46489023"
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
  
#### <a name="parameters"></a>Parâmetros  
 `flags`  
 [in] Uma [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) membro de enumeração que especifica se a IL (linguagem intermediária) definida pela solicitação do ReJIT do criador de perfil é incluída no quadro.  
  
 `ppCode`  
 [out] Um ponteiro para o endereço de um objeto de "ICorDebugCode" que representa o código que este registro de ativação está em execução.  
  
## <a name="remarks"></a>Comentários  
 Esse método é semelhante para o [icordebugframe:: Getcode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) método, exceto que ele acessa opcionalmente definido pela solicitação do ReJIT do criador de perfil de código. Chamar esse método com um `flags` valor de `ILCODE_ORIGINAL_IL` é equivalente a chamar [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); se o método for instrumentado, sua IL não estará acessível. `ILCODE_REJIT_IL` permite que o depurador acesse a IL definida pela solicitação ReJIT do criador de perfil. Se o IL não for instrumentado, `ppCode` está **nulo**, e o método retornará `S_OK`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugILFrame4](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ReJIT: Um guia de instruções](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
