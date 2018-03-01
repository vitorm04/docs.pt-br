---
title: "ICorDebugILFrame4::Método GetCodeEx"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e5d1d480014e90d3fea9790b10e0dace5a0847ad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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
 [in] Um [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) membro de enumeração que especifica se a linguagem intermediária (IL) definida pela solicitação de ReJIT do criador de perfil está incluída no quadro.  
  
 `ppCode`  
 [out] Um ponteiro para o endereço de um objeto de "ICorDebugCode" que representa o código que está em execução deste quadro de pilhas.  
  
## <a name="remarks"></a>Comentários  
 Esse método é semelhante do [Icordebugframe](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) método, exceto que ele acessa opcionalmente definido pela solicitação de ReJIT do criador de perfil de código. Chamar este método com um `flags` valor `ILCODE_ORIGINAL_IL` é equivalente a chamar [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); se o método é instrumentado, seu IL não estará acessível. `ILCODE_REJIT_IL` permite que o depurador acesse a IL definida pela solicitação ReJIT do criador de perfil. Se o IL não está instrumentado, `ppCode` é **nulo**, e o método retornará `S_OK`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugILFrame4](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ReJIT: Um guia de instruções](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
