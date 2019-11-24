---
title: Método IMetaDataImport::ResolveTypeRef
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResolveTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResolveTypeRef
helpviewer_keywords:
- ResolveTypeRef method [.NET Framework metadata]
- IMetaDataImport::ResolveTypeRef method [.NET Framework metadata]
ms.assetid: 556bccfb-61bc-4761-b1d5-de4b1c18a38f
topic_type:
- apiref
ms.openlocfilehash: 800b15bb75e74898cee9d838900ea14b60620940
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431476"
---
# <a name="imetadataimportresolvetyperef-method"></a><span data-ttu-id="df61a-102">Método IMetaDataImport::ResolveTypeRef</span><span class="sxs-lookup"><span data-stu-id="df61a-102">IMetaDataImport::ResolveTypeRef Method</span></span>
<span data-ttu-id="df61a-103">Resolves a <xref:System.Type> reference represented by the specified TypeRef token.</span><span class="sxs-lookup"><span data-stu-id="df61a-103">Resolves a <xref:System.Type> reference represented by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df61a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="df61a-104">Syntax</span></span>  
  
```cpp  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df61a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="df61a-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="df61a-106">[in] The TypeRef metadata token to return the referenced type information for.</span><span class="sxs-lookup"><span data-stu-id="df61a-106">[in] The TypeRef metadata token to return the referenced type information for.</span></span>  
  
 `riid`  
 <span data-ttu-id="df61a-107">[in] The IID of the interface to return in `ppIScope`.</span><span class="sxs-lookup"><span data-stu-id="df61a-107">[in] The IID of the interface to return in `ppIScope`.</span></span> <span data-ttu-id="df61a-108">Typically, this would be IID_IMetaDataImport.</span><span class="sxs-lookup"><span data-stu-id="df61a-108">Typically, this would be IID_IMetaDataImport.</span></span>  
  
 `ppIScope`  
 <span data-ttu-id="df61a-109">[out] An interface to the module scope in which the referenced type is defined.</span><span class="sxs-lookup"><span data-stu-id="df61a-109">[out] An interface to the module scope in which the referenced type is defined.</span></span>  
  
 `ptd`  
 <span data-ttu-id="df61a-110">[out] A pointer to a TypeDef token that represents the referenced type.</span><span class="sxs-lookup"><span data-stu-id="df61a-110">[out] A pointer to a TypeDef token that represents the referenced type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df61a-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="df61a-111">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="df61a-112">Do not use this method if multiple application domains are loaded.</span><span class="sxs-lookup"><span data-stu-id="df61a-112">Do not use this method if multiple application domains are loaded.</span></span> <span data-ttu-id="df61a-113">The method does not respect application domain boundaries.</span><span class="sxs-lookup"><span data-stu-id="df61a-113">The method does not respect application domain boundaries.</span></span> <span data-ttu-id="df61a-114">If multiple versions of an assembly are loaded, and they contain the same type with the same namespace, the method returns the module scope of the first type it finds.</span><span class="sxs-lookup"><span data-stu-id="df61a-114">If multiple versions of an assembly are loaded, and they contain the same type with the same namespace, the method returns the module scope of the first type it finds.</span></span>  
  
 <span data-ttu-id="df61a-115">The `ResolveTypeRef` method searches for the type definition in other modules.</span><span class="sxs-lookup"><span data-stu-id="df61a-115">The `ResolveTypeRef` method searches for the type definition in other modules.</span></span> <span data-ttu-id="df61a-116">If the type definition is found, `ResolveTypeRef` returns an interface to that module scope as well as the TypeDef token for the type.</span><span class="sxs-lookup"><span data-stu-id="df61a-116">If the type definition is found, `ResolveTypeRef` returns an interface to that module scope as well as the TypeDef token for the type.</span></span>  
  
 <span data-ttu-id="df61a-117">If the type reference to be resolved has a resolution scope of AssemblyRef, the `ResolveTypeRef` method searches for a match only in the metadata scopes that have already been opened with calls to either the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method or the [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="df61a-117">If the type reference to be resolved has a resolution scope of AssemblyRef, the `ResolveTypeRef` method searches for a match only in the metadata scopes that have already been opened with calls to either the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method or the [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method.</span></span> <span data-ttu-id="df61a-118">This is because `ResolveTypeRef` cannot determine from only the AssemblyRef scope where on disk or in the global assembly cache the assembly is stored.</span><span class="sxs-lookup"><span data-stu-id="df61a-118">This is because `ResolveTypeRef` cannot determine from only the AssemblyRef scope where on disk or in the global assembly cache the assembly is stored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df61a-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="df61a-119">Requirements</span></span>  
 <span data-ttu-id="df61a-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df61a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df61a-121">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="df61a-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="df61a-122">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="df61a-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="df61a-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df61a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df61a-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df61a-124">See also</span></span>

- [<span data-ttu-id="df61a-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="df61a-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="df61a-126">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="df61a-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
