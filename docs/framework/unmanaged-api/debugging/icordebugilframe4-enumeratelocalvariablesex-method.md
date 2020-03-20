---
title: ICorDebugILFrame4::Método EnumerateLocalVariablesEx
ms.date: 03/30/2017
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
ms.openlocfilehash: 341a86f4c1c8367f979e193a6284bf89f1b03ca0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178796"
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
  
## <a name="parameters"></a>parâmetros  
 `flags`  
 [em] Um membro de enumeração [ILCodeKind](ilcodekind-enumeration.md) que especifica se as variáveis adicionadas na instrumentação ReJIT do profiler estão incluídas no quadro.  
  
 `ppValueEnum`  
 [fora] Um ponteiro para o endereço de um objeto "ICorDebugValueEnum" que é o enumerador para as variáveis locais neste quadro.  
  
## <a name="remarks"></a>Comentários  
 Este método é semelhante ao método [EnumerateLocalVariables,](icordebugilframe-enumeratelocalvariables-method.md) exceto que ele acessa opcionalmente variáveis adicionadas na instrumentação ReJIT profiler. A `flags` `ILCODE_ORIGINAL_IL` configuração é equivalente a chamar [ICorDebugILFrame::EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md). Configurar `flags` para `ILCODE_REJIT_IL` permite ao depurador acessar as variáveis locais incluídas na instrumentação ReJIT do criador de perfis. Se a linguagem intermediária (IL) não estiver instrumentada, a enumeração estará vazia e o método retornará `S_OK`.  
  
 O enumerador poderá não incluir todas as variáveis locais no método em execução, considerando que algumas delas podem não estar ativas.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebugILFrame4](icordebugilframe4-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
- [ReJIT: Um Guia de Como Fazer](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
