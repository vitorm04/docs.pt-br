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
ms.openlocfilehash: b9e488a512ad506a8975bfff44ae02cd84c29f74
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861691"
---
# <a name="icorprofilerinfo7applymetadata-method"></a><span data-ttu-id="a9878-102">Método ICorProfilerInfo7:: ApplyMetaData</span><span class="sxs-lookup"><span data-stu-id="a9878-102">ICorProfilerInfo7::ApplyMetaData Method</span></span>
<span data-ttu-id="a9878-103">[Com suporte no .NET Framework 4.6.1 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="a9878-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="a9878-104">Aplica os metadados recentemente definidos pelos métodos de `IMetadataEmit::Define*` a um módulo especificado.</span><span class="sxs-lookup"><span data-stu-id="a9878-104">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9878-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a9878-105">Syntax</span></span>  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9878-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a9878-106">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="a9878-107">no O identificador do módulo cujos metadados foram alterados.</span><span class="sxs-lookup"><span data-stu-id="a9878-107">[in] The identifier of the module whose metadata was changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9878-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="a9878-108">Remarks</span></span>  
 <span data-ttu-id="a9878-109">Se forem feitas alterações de metadados após o retorno de chamada [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) , você deverá chamar esse método antes de usar os novos metadados.</span><span class="sxs-lookup"><span data-stu-id="a9878-109">If metadata changes are made after the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback, you must call this method before using the new metadata.</span></span>  
  
 <span data-ttu-id="a9878-110">`ApplyMetaData` só dá suporte à adição dos seguintes tipos de metadados:</span><span class="sxs-lookup"><span data-stu-id="a9878-110">`ApplyMetaData` only supports adding the following types of metadata:</span></span>  
  
- <span data-ttu-id="a9878-111">`AssemblyRef` registros, que você cria chamando o [IMetaDataAssemblyEmit::D efineassemblyref](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span><span class="sxs-lookup"><span data-stu-id="a9878-111">`AssemblyRef` records, which you create by calling the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span></span> <span data-ttu-id="a9878-112">método.</span><span class="sxs-lookup"><span data-stu-id="a9878-112">method.</span></span>  
  
- <span data-ttu-id="a9878-113">`TypeRef` registros, que você cria chamando o método [IMetaDataEmit::D efinetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a9878-113">`TypeRef` records, which you create by calling the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) method.</span></span>  
  
- <span data-ttu-id="a9878-114">`TypeSpec` registros, que você cria chamando o método [IMetaDataEmit:: GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a9878-114">`TypeSpec` records, which you create by calling the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
- <span data-ttu-id="a9878-115">`MemberRef` registros, que você cria chamando o método [IMetaDataEmit::D efinememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a9878-115">`MemberRef` records, which you create by calling the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method.</span></span>  
  
- <span data-ttu-id="a9878-116">`MemberSpec` registros, que você cria chamando o método [IMetaDataEmit2::D efinemethodspec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a9878-116">`MemberSpec` records, which you create by calling the [IMetaDataEmit2::DefineMethodSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) method.</span></span>  
  
- <span data-ttu-id="a9878-117">`UserString` registros, que você cria chamando o método [IMetaDataEmit::D efineuserstring](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a9878-117">`UserString` records, which you create by calling the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span>  

<span data-ttu-id="a9878-118">A partir do .NET Core 3,0, o `ApplyMetaData` também oferece suporte aos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="a9878-118">Starting with .NET Core 3.0, `ApplyMetaData` also supports the following types:</span></span>

- <span data-ttu-id="a9878-119">`TypeDef` registros, que você cria chamando o método [IMetaDataEmit::D efinetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a9878-119">`TypeDef` records, which you create by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method.</span></span>

- <span data-ttu-id="a9878-120">`MethodDef` registros, que você cria chamando o método [IMetaDataEmit::D efinemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a9878-120">`MethodDef` records, which you create by calling the [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md) method.</span></span> <span data-ttu-id="a9878-121">No entanto, não há suporte para a adição de métodos virtuais a um tipo existente.</span><span class="sxs-lookup"><span data-stu-id="a9878-121">However, adding virtual methods to an existing type is not supported.</span></span> <span data-ttu-id="a9878-122">Métodos virtuais devem ser adicionados antes do retorno de chamada [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a9878-122">Virtual methods must be added before the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="a9878-123">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="a9878-123">Requirements</span></span>  
 <span data-ttu-id="a9878-124">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9878-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9878-125">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a9878-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a9878-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9878-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9878-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9878-127">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9878-128">Veja também</span><span class="sxs-lookup"><span data-stu-id="a9878-128">See also</span></span>

- [<span data-ttu-id="a9878-129">Interface ICorProfilerInfo7</span><span class="sxs-lookup"><span data-stu-id="a9878-129">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)
