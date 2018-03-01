---
title: "ICorDebugILFrame4::Método EnumerateLocalVariablesEx"
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
- ICorDebugILFrame4.EnumerateLocalVariablesEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6f60aae6-70ec-4c4c-963a-138df98c4668
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c82ecd9045deb772e31e549bf1050f85b148fd0b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a>ICorDebugILFrame4::Método EnumerateLocalVariablesEx
[Com suporte no .NET Framework 4.5.2 e versões posteriores]  
  
 Obtém um enumerador da variável local no quadro e, opcionalmente, inclui variáveis incluídas na instrumentação ReJIT do criador de perfis.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `flags`  
 [in] Um [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) membro de enumeração que especifica se as variáveis adicionadas no criador de perfil de instrumentação ReJIT são incluídas no quadro.  
  
 `ppValueEnum`  
 [out] Um ponteiro para o endereço de um objeto de "ICorDebugValueEnum" é o enumerador para as variáveis locais nesse quadro.  
  
## <a name="remarks"></a>Comentários  
 Esse método é semelhante do [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md) método, exceto que ele acessa opcionalmente variáveis adicionadas ReJIT instrumentação do criador de perfil. Configuração `flags` para `ILCODE_ORIGINAL_IL` é equivalente a chamar [Icordebugilframe](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md). Configurar `flags` para `ILCODE_REJIT_IL` permite ao depurador acessar as variáveis locais incluídas na instrumentação ReJIT do criador de perfis. Se a linguagem intermediária (IL) não estiver instrumentada, a enumeração estará vazia e o método retornará `S_OK`.  
  
 O enumerador poderá não incluir todas as variáveis locais no método em execução, considerando que algumas delas podem não estar ativas.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugILFrame4](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ReJIT: Um guia de instruções](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
