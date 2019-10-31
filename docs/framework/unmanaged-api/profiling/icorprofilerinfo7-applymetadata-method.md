---
title: 'Método ICorProfilerInfo7:: ApplyMetaData'
ms.date: 02/15/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo7.ApplyMetaData
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: a1bfb649-4584-4d35-b3e6-8fe59b53992a
ms.openlocfilehash: 00d9bef1e2b59a2d2207d1e343380e0e81bee848
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130358"
---
# <a name="icorprofilerinfo7applymetadata-method"></a><span data-ttu-id="fbfea-102">Método ICorProfilerInfo7:: ApplyMetaData</span><span class="sxs-lookup"><span data-stu-id="fbfea-102">ICorProfilerInfo7::ApplyMetaData Method</span></span>
<span data-ttu-id="fbfea-103">[Com suporte no .NET Framework 4.6.1 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="fbfea-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="fbfea-104">Aplica os metadados recentemente definidos pelos métodos de `IMetadataEmit::Define*` a um módulo especificado.</span><span class="sxs-lookup"><span data-stu-id="fbfea-104">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbfea-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fbfea-105">Syntax</span></span>  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fbfea-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fbfea-106">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="fbfea-107">no O identificador do módulo cujos metadados foram alterados.</span><span class="sxs-lookup"><span data-stu-id="fbfea-107">[in] The identifier of the module whose metadata was changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbfea-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="fbfea-108">Remarks</span></span>  
 <span data-ttu-id="fbfea-109">Se forem feitas alterações de metadados após o retorno de chamada [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) , você deverá chamar esse método antes de usar os novos metadados.</span><span class="sxs-lookup"><span data-stu-id="fbfea-109">If metadata changes are made after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback, you must call this method before using the new metadata.</span></span>  
  
 <span data-ttu-id="fbfea-110">`ApplyMetaData` só dá suporte à adição dos seguintes tipos de metadados:</span><span class="sxs-lookup"><span data-stu-id="fbfea-110">`ApplyMetaData` only supports adding the following types of metadata:</span></span>  
  
- <span data-ttu-id="fbfea-111">`AssemblyRef` registros, que você cria chamando o [IMetaDataAssemblyEmit::D efineassemblyref](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span><span class="sxs-lookup"><span data-stu-id="fbfea-111">`AssemblyRef` records, which you create by calling the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span></span> <span data-ttu-id="fbfea-112">método.</span><span class="sxs-lookup"><span data-stu-id="fbfea-112">method.</span></span>  
  
- <span data-ttu-id="fbfea-113">`TypeRef` registros, que você cria chamando o método [IMetaDataEmit::D efinetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fbfea-113">`TypeRef` records, which you create by calling the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) method.</span></span>  
  
- <span data-ttu-id="fbfea-114">`TypeSpec` registros, que você cria chamando o método [IMetaDataEmit:: GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fbfea-114">`TypeSpec` records, which you create by calling the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
- <span data-ttu-id="fbfea-115">`MemberRef` registros, que você cria chamando o método [IMetaDataEmit::D efinememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fbfea-115">`MemberRef` records, which you create by calling the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method.</span></span>  
  
- <span data-ttu-id="fbfea-116">`MemberSpec` registros, que você cria chamando o método [IMetaDataEmit2::D efinemethodspec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fbfea-116">`MemberSpec` records, which you create by calling the [IMetaDataEmit2::DefineMethodSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) method.</span></span>  
  
- <span data-ttu-id="fbfea-117">`UserString` registros, que você cria chamando o método [IMetaDataEmit::D efineuserstring](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fbfea-117">`UserString` records, which you create by calling the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span>  

<span data-ttu-id="fbfea-118">A partir do .NET Core 3,0, o `ApplyMetaData` também oferece suporte aos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="fbfea-118">Starting with .NET Core 3.0, `ApplyMetaData` also supports the following types:</span></span>

- <span data-ttu-id="fbfea-119">`TypeDef` registros, que você cria chamando o método [IMetaDataEmit::D efinetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fbfea-119">`TypeDef` records, which you create by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method.</span></span>

- <span data-ttu-id="fbfea-120">`MethodDef` registros, que você cria chamando o método [IMetaDataEmit::D efinemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fbfea-120">`MethodDef` records, which you create by calling the [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md) method.</span></span> <span data-ttu-id="fbfea-121">No entanto, não há suporte para a adição de métodos virtuais a um tipo existente.</span><span class="sxs-lookup"><span data-stu-id="fbfea-121">However, adding virtual methods to an existing type is not supported.</span></span> <span data-ttu-id="fbfea-122">Métodos virtuais devem ser adicionados antes do retorno de chamada [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fbfea-122">Virtual methods must be added before the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="fbfea-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fbfea-123">Requirements</span></span>  
 <span data-ttu-id="fbfea-124">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbfea-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbfea-125">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="fbfea-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fbfea-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fbfea-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fbfea-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbfea-127">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbfea-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fbfea-128">See also</span></span>

- [<span data-ttu-id="fbfea-129">Interface ICorProfilerInfo7</span><span class="sxs-lookup"><span data-stu-id="fbfea-129">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
