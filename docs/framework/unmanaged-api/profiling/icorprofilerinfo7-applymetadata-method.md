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
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo7applymetadata-method"></a><span data-ttu-id="64eea-102">Método ICorProfilerInfo7::ApplyMetaData</span><span class="sxs-lookup"><span data-stu-id="64eea-102">ICorProfilerInfo7::ApplyMetaData Method</span></span>
<span data-ttu-id="64eea-103">[Com suporte no .NET Framework 4.6.1 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="64eea-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="64eea-104">Aplica-se os metadados recentemente definido pelo `IMetadataEmit::Define*` métodos para um módulo especificado.</span><span class="sxs-lookup"><span data-stu-id="64eea-104">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64eea-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="64eea-105">Syntax</span></span>  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="64eea-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="64eea-106">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="64eea-107">[in] O identificador do módulo cujos metadados foi alterado.</span><span class="sxs-lookup"><span data-stu-id="64eea-107">[in] The identifier of the module whose metadata was changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64eea-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="64eea-108">Remarks</span></span>  
 <span data-ttu-id="64eea-109">Se forem feitas alterações de metadados após o [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) retorno de chamada, você deve chamar esse método antes de usar os novos metadados.</span><span class="sxs-lookup"><span data-stu-id="64eea-109">If metadata changes are made after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback, you must call this method before using the new metadata.</span></span>  
  
 <span data-ttu-id="64eea-110">`ApplyMetaData` só dá suporte a adicionar os seguintes tipos de metadados:</span><span class="sxs-lookup"><span data-stu-id="64eea-110">`ApplyMetaData` only supports adding the following types of metadata:</span></span>  
  
-   <span data-ttu-id="64eea-111">`AssemblyRef` registros que você criar chamando o [: Defineassemblyref](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span><span class="sxs-lookup"><span data-stu-id="64eea-111">`AssemblyRef` records, which you create by calling the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span></span> <span data-ttu-id="64eea-112">método.</span><span class="sxs-lookup"><span data-stu-id="64eea-112">method.</span></span>  
  
-   <span data-ttu-id="64eea-113">`TypeRef` registros que você criar chamando o [Definetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="64eea-113">`TypeRef` records, which you create by calling the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) method.</span></span>  
  
-   <span data-ttu-id="64eea-114">`TypeSpec` registros que você criar chamando o [: Gettokenfromtypespec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="64eea-114">`TypeSpec` records, which you create by calling the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
-   <span data-ttu-id="64eea-115">`MemberRef` registros que você criar chamando o [: Definememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="64eea-115">`MemberRef` records, which you create by calling the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method.</span></span>  
  
-   <span data-ttu-id="64eea-116">`MemberSpec` registros que você criar chamando o [IMetaDataEmit2::DefineMethodSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="64eea-116">`MemberSpec` records, which you create by calling the [IMetaDataEmit2::DefineMethodSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) method.</span></span>  
  
-   <span data-ttu-id="64eea-117">`UserString` registros que você criar chamando o [: Defineuserstring](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="64eea-117">`UserString` records, which you create by calling the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64eea-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="64eea-118">Requirements</span></span>  
 <span data-ttu-id="64eea-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64eea-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64eea-120">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="64eea-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="64eea-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64eea-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64eea-122">**Versões do .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64eea-122">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64eea-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64eea-123">See Also</span></span>  
 [<span data-ttu-id="64eea-124">Interface ICorProfilerInfo7</span><span class="sxs-lookup"><span data-stu-id="64eea-124">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
