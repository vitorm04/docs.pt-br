---
title: ICorProfilerAssemblyReferenceProvider::Método AddAssemblyReference
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerAssemblyReferenceProvider.AddAssemblyReference
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 3d5af8e7-c337-48f4-9fa6-97c83878b9b1
topic_type:
- apiref
ms.openlocfilehash: 2357e5348192db5d41adfe1176300359440aeee3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866722"
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a>ICorProfilerAssemblyReferenceProvider::Método AddAssemblyReference
[Com suporte no .NET Framework 4.5.2 e versões posteriores]  
  
 Informa o Common Language Runtime (CLR) de uma referência de assembly que o criador de perfil planeja adicionar ao retorno de chamada [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
## <a name="parameters"></a>Parâmetros

- `pAssemblyRefInfo`

  Um ponteiro para uma estrutura de [COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md) que fornece ao CLR informações sobre uma referência de assembly que deve ser considerada ao executar uma movimentação de fechamento de referência de assembly.
  
## <a name="remarks"></a>Comentários  
 O criador de perfil chama esse método para cada assembly de destino que planeja fazer referência a partir do assembly especificado no argumento `wszAssemblyPath` do retorno de chamada [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) . O objeto da interface [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) é passado para o retorno de chamada [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) do criador de perfil, juntamente com o caminho e o nome do assembly no argumento `wszAssemblyPath`.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md)
- [Método GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md)
- [Método ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)
