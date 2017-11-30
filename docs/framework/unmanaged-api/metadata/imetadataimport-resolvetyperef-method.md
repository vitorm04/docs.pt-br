---
title: "Método IMetaDataImport::ResolveTypeRef"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.ResolveTypeRef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::ResolveTypeRef
helpviewer_keywords:
- ResolveTypeRef method [.NET Framework metadata]
- IMetaDataImport::ResolveTypeRef method [.NET Framework metadata]
ms.assetid: 556bccfb-61bc-4761-b1d5-de4b1c18a38f
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 390387abef5c48b4842adcfbfca126bb8292cc28
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportresolvetyperef-method"></a><span data-ttu-id="42a55-102">Método IMetaDataImport::ResolveTypeRef</span><span class="sxs-lookup"><span data-stu-id="42a55-102">IMetaDataImport::ResolveTypeRef Method</span></span>
<span data-ttu-id="42a55-103">Resolve um <xref:System.Type> referência representada pelo token TypeRef especificado.</span><span class="sxs-lookup"><span data-stu-id="42a55-103">Resolves a <xref:System.Type> reference represented by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42a55-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="42a55-104">Syntax</span></span>  
  
```  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="42a55-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="42a55-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="42a55-106">[in] O token de metadados de TypeRef para retornar as informações de tipo referenciado.</span><span class="sxs-lookup"><span data-stu-id="42a55-106">[in] The TypeRef metadata token to return the referenced type information for.</span></span>  
  
 `riid`  
 <span data-ttu-id="42a55-107">[in] O IID da interface para retornar em `ppIScope`.</span><span class="sxs-lookup"><span data-stu-id="42a55-107">[in] The IID of the interface to return in `ppIScope`.</span></span> <span data-ttu-id="42a55-108">Normalmente, isso seria IID_IMetaDataImport.</span><span class="sxs-lookup"><span data-stu-id="42a55-108">Typically, this would be IID_IMetaDataImport.</span></span>  
  
 `ppIScope`  
 <span data-ttu-id="42a55-109">[out] Uma interface para o escopo de módulo no qual o tipo referenciado é definido.</span><span class="sxs-lookup"><span data-stu-id="42a55-109">[out] An interface to the module scope in which the referenced type is defined.</span></span>  
  
 `ptd`  
 <span data-ttu-id="42a55-110">[out] Um ponteiro para um token de TypeDef que representa o tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="42a55-110">[out] A pointer to a TypeDef token that represents the referenced type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42a55-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="42a55-111">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="42a55-112">Não use esse método se vários domínios de aplicativo são carregados.</span><span class="sxs-lookup"><span data-stu-id="42a55-112">Do not use this method if multiple application domains are loaded.</span></span> <span data-ttu-id="42a55-113">O método não respeita os limites de domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="42a55-113">The method does not respect application domain boundaries.</span></span> <span data-ttu-id="42a55-114">Se várias versões de um assembly são carregadas e contêm o mesmo tipo com o mesmo namespace, o método retorna o escopo de módulo do tipo primeiro encontra.</span><span class="sxs-lookup"><span data-stu-id="42a55-114">If multiple versions of an assembly are loaded, and they contain the same type with the same namespace, the method returns the module scope of the first type it finds.</span></span>  
  
 <span data-ttu-id="42a55-115">O `ResolveTypeRef` pesquisas de método para a definição de tipo em outros módulos.</span><span class="sxs-lookup"><span data-stu-id="42a55-115">The `ResolveTypeRef` method searches for the type definition in other modules.</span></span> <span data-ttu-id="42a55-116">Se a definição do tipo for encontrada, `ResolveTypeRef` retorna uma interface para esse escopo de módulo, bem como o token de TypeDef para o tipo.</span><span class="sxs-lookup"><span data-stu-id="42a55-116">If the type definition is found, `ResolveTypeRef` returns an interface to that module scope as well as the TypeDef token for the type.</span></span>  
  
 <span data-ttu-id="42a55-117">Se a referência de tipo a ser resolvido tem um escopo de resolução de AssemblyRef, o `ResolveTypeRef` método procura uma correspondência somente nos escopos de metadados que já foi aberto com chamadas para o o [Imetadatadispenser](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)método ou o [Imetadatadispenser](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="42a55-117">If the type reference to be resolved has a resolution scope of AssemblyRef, the `ResolveTypeRef` method searches for a match only in the metadata scopes that have already been opened with calls to either the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method or the [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method.</span></span> <span data-ttu-id="42a55-118">Isso ocorre porque `ResolveTypeRef` não é possível determinar de apenas o escopo de AssemblyRef onde no disco ou no cache de assembly global o assembly é armazenado.</span><span class="sxs-lookup"><span data-stu-id="42a55-118">This is because `ResolveTypeRef` cannot determine from only the AssemblyRef scope where on disk or in the global assembly cache the assembly is stored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42a55-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="42a55-119">Requirements</span></span>  
 <span data-ttu-id="42a55-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42a55-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42a55-121">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="42a55-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="42a55-122">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="42a55-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="42a55-123">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42a55-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42a55-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="42a55-124">See Also</span></span>  
 [<span data-ttu-id="42a55-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="42a55-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="42a55-126">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="42a55-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
