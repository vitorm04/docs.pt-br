---
title: Método ICorProfilerInfo7::ApplyMetaData
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aff6f63bb9f41fe45b22854787667070929bf987
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213760"
---
# <a name="icorprofilerinfo7applymetadata-method"></a><span data-ttu-id="fdd67-102">Método ICorProfilerInfo7::ApplyMetaData</span><span class="sxs-lookup"><span data-stu-id="fdd67-102">ICorProfilerInfo7::ApplyMetaData Method</span></span>
<span data-ttu-id="fdd67-103">[Com suporte no .NET Framework 4.6.1 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="fdd67-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="fdd67-104">Aplica-se os metadados recentemente definido pelo `IMetadataEmit::Define*` métodos para um módulo especificado.</span><span class="sxs-lookup"><span data-stu-id="fdd67-104">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdd67-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fdd67-105">Syntax</span></span>  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fdd67-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fdd67-106">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="fdd67-107">[in] O identificador do módulo cujos metadados foram alterados.</span><span class="sxs-lookup"><span data-stu-id="fdd67-107">[in] The identifier of the module whose metadata was changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fdd67-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="fdd67-108">Remarks</span></span>  
 <span data-ttu-id="fdd67-109">Se forem feitas alterações de metadados após o [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) retorno de chamada, você deve chamar esse método antes de usar os novos metadados.</span><span class="sxs-lookup"><span data-stu-id="fdd67-109">If metadata changes are made after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback, you must call this method before using the new metadata.</span></span>  
  
 `ApplyMetaData` <span data-ttu-id="fdd67-110">só dá suporte a adicionar os seguintes tipos de metadados:</span><span class="sxs-lookup"><span data-stu-id="fdd67-110">only supports adding the following types of metadata:</span></span>  
  
-   `AssemblyRef` <span data-ttu-id="fdd67-111">registros que você crie chamando o [imetadataassemblyemit:: Defineassemblyref](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span><span class="sxs-lookup"><span data-stu-id="fdd67-111">records, which you create by calling the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span></span> <span data-ttu-id="fdd67-112">método.</span><span class="sxs-lookup"><span data-stu-id="fdd67-112">method.</span></span>  
  
-   `TypeRef` <span data-ttu-id="fdd67-113">registros que você crie chamando o [imetadataemit:: Definetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="fdd67-113">records, which you create by calling the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) method.</span></span>  
  
-   `TypeSpec` <span data-ttu-id="fdd67-114">registros que você crie chamando o [imetadataemit:: Gettokenfromtypespec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="fdd67-114">records, which you create by calling the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
-   `MemberRef` <span data-ttu-id="fdd67-115">registros que você crie chamando o [imetadataemit:: Definememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="fdd67-115">records, which you create by calling the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method.</span></span>  
  
-   `MemberSpec` <span data-ttu-id="fdd67-116">registros que você crie chamando o [IMetaDataEmit2::DefineMethodSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="fdd67-116">records, which you create by calling the [IMetaDataEmit2::DefineMethodSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) method.</span></span>  
  
-   `UserString` <span data-ttu-id="fdd67-117">registros que você crie chamando o [imetadataemit:: Defineuserstring](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="fdd67-117">records, which you create by calling the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span>  

<span data-ttu-id="fdd67-118">Começando com o .NET Core 3.0, `ApplyMetaData` também suporta os seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="fdd67-118">Starting with .NET Core 3.0, `ApplyMetaData` also supports the following types:</span></span>

- `TypeDef` <span data-ttu-id="fdd67-119">registros que você crie chamando o [imetadataemit:: Definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="fdd67-119">records, which you create by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method.</span></span>

- `MethodDef` <span data-ttu-id="fdd67-120">registros que você crie chamando o [imetadataemit:: Definemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="fdd67-120">records, which you create by calling the [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md) method.</span></span> <span data-ttu-id="fdd67-121">No entanto, não há suporte para adição de métodos virtuais a um tipo existente.</span><span class="sxs-lookup"><span data-stu-id="fdd67-121">However, adding virtual methods to an existing type is not supported.</span></span> <span data-ttu-id="fdd67-122">Métodos virtuais devem ser adicionados antes do [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="fdd67-122">Virtual methods must be added before the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="fdd67-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fdd67-123">Requirements</span></span>  
 <span data-ttu-id="fdd67-124">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdd67-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdd67-125">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fdd67-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fdd67-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fdd67-126">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="fdd67-127">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="fdd67-127">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fdd67-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fdd67-128">See also</span></span>

- [<span data-ttu-id="fdd67-129">Interface ICorProfilerInfo7</span><span class="sxs-lookup"><span data-stu-id="fdd67-129">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
