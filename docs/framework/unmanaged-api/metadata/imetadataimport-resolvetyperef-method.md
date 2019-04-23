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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f929e6b338d4fd48b2a6ef9588523377e0dd8faa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59096056"
---
# <a name="imetadataimportresolvetyperef-method"></a><span data-ttu-id="e4b11-102">Método IMetaDataImport::ResolveTypeRef</span><span class="sxs-lookup"><span data-stu-id="e4b11-102">IMetaDataImport::ResolveTypeRef Method</span></span>
<span data-ttu-id="e4b11-103">Resolve um <xref:System.Type> referência representada pelo token TypeRef especificado.</span><span class="sxs-lookup"><span data-stu-id="e4b11-103">Resolves a <xref:System.Type> reference represented by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4b11-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e4b11-104">Syntax</span></span>  
  
```  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4b11-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e4b11-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="e4b11-106">[in] O token de metadados TypeRef para retornar as informações de tipo referenciado.</span><span class="sxs-lookup"><span data-stu-id="e4b11-106">[in] The TypeRef metadata token to return the referenced type information for.</span></span>  
  
 `riid`  
 <span data-ttu-id="e4b11-107">[in] O IID da interface para retornar em `ppIScope`.</span><span class="sxs-lookup"><span data-stu-id="e4b11-107">[in] The IID of the interface to return in `ppIScope`.</span></span> <span data-ttu-id="e4b11-108">Normalmente, isso seria IID_IMetaDataImport.</span><span class="sxs-lookup"><span data-stu-id="e4b11-108">Typically, this would be IID_IMetaDataImport.</span></span>  
  
 `ppIScope`  
 <span data-ttu-id="e4b11-109">[out] Uma interface para o escopo de módulo no qual o tipo referenciado é definido.</span><span class="sxs-lookup"><span data-stu-id="e4b11-109">[out] An interface to the module scope in which the referenced type is defined.</span></span>  
  
 `ptd`  
 <span data-ttu-id="e4b11-110">[out] Um ponteiro para um token de TypeDef que representa o tipo referenciado.</span><span class="sxs-lookup"><span data-stu-id="e4b11-110">[out] A pointer to a TypeDef token that represents the referenced type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4b11-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="e4b11-111">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e4b11-112">Não use esse método se vários domínios de aplicativo são carregados.</span><span class="sxs-lookup"><span data-stu-id="e4b11-112">Do not use this method if multiple application domains are loaded.</span></span> <span data-ttu-id="e4b11-113">O método não respeita os limites de domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e4b11-113">The method does not respect application domain boundaries.</span></span> <span data-ttu-id="e4b11-114">Se várias versões de um assembly são carregadas e que eles contêm o mesmo tipo com o mesmo namespace, o método retorna o escopo de módulo do primeiro tipo, que ele localiza.</span><span class="sxs-lookup"><span data-stu-id="e4b11-114">If multiple versions of an assembly are loaded, and they contain the same type with the same namespace, the method returns the module scope of the first type it finds.</span></span>  
  
 <span data-ttu-id="e4b11-115">O `ResolveTypeRef` pesquisas de método para a definição de tipo em outros módulos.</span><span class="sxs-lookup"><span data-stu-id="e4b11-115">The `ResolveTypeRef` method searches for the type definition in other modules.</span></span> <span data-ttu-id="e4b11-116">Se a definição de tipo for encontrada, `ResolveTypeRef` retorna uma interface para esse escopo de módulo, bem como o token de TypeDef para o tipo.</span><span class="sxs-lookup"><span data-stu-id="e4b11-116">If the type definition is found, `ResolveTypeRef` returns an interface to that module scope as well as the TypeDef token for the type.</span></span>  
  
 <span data-ttu-id="e4b11-117">Se a referência de tipo a serem resolvidas tem um escopo de resolução de AssemblyRef, o `ResolveTypeRef` método procura uma correspondência somente em escopos metadados que já foi aberto com chamadas para qualquer um de [imetadatadispenser:: Openscope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)método ou o [imetadatadispenser:: Openscopeonmemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="e4b11-117">If the type reference to be resolved has a resolution scope of AssemblyRef, the `ResolveTypeRef` method searches for a match only in the metadata scopes that have already been opened with calls to either the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method or the [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method.</span></span> <span data-ttu-id="e4b11-118">Isso ocorre porque `ResolveTypeRef` não é possível determinar de apenas o escopo de AssemblyRef onde no disco ou no cache de assembly global assembly é armazenado.</span><span class="sxs-lookup"><span data-stu-id="e4b11-118">This is because `ResolveTypeRef` cannot determine from only the AssemblyRef scope where on disk or in the global assembly cache the assembly is stored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4b11-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e4b11-119">Requirements</span></span>  
 <span data-ttu-id="e4b11-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4b11-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4b11-121">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e4b11-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e4b11-122">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e4b11-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e4b11-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4b11-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4b11-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4b11-124">See also</span></span>

- [<span data-ttu-id="e4b11-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="e4b11-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="e4b11-126">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="e4b11-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
