---
title: Método ICorProfilerInfo7::ApplyMetaData
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerInfo7.ApplyMetaData
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: a1bfb649-4584-4d35-b3e6-8fe59b53992a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b8b6ba429a45c92dc6b6b5dcaa7c8a35b47385f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo7applymetadata-method"></a>Método ICorProfilerInfo7::ApplyMetaData
[Com suporte no .NET Framework 4.6.1 e versões posteriores]  
  
 Aplica-se os metadados recentemente definido pelo `IMetadataEmit::Define*` métodos para um módulo especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `moduleID`  
 [in] O identificador do módulo cujos metadados foi alterado.  
  
## <a name="remarks"></a>Comentários  
 Se forem feitas alterações de metadados após o [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) retorno de chamada, você deve chamar esse método antes de usar os novos metadados.  
  
 `ApplyMetaData` só dá suporte a adicionar os seguintes tipos de metadados:  
  
-   `AssemblyRef` registros que você criar chamando o [: Defineassemblyref](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md). método.  
  
-   `TypeRef` registros que você criar chamando o [Definetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) método.  
  
-   `TypeSpec` registros que você criar chamando o [: Gettokenfromtypespec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) método.  
  
-   `MemberRef` registros que você criar chamando o [: Definememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) método.  
  
-   `MemberSpec` registros que você criar chamando o [IMetaDataEmit2::DefineMethodSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) método.  
  
-   `UserString` registros que você criar chamando o [: Defineuserstring](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo7](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
