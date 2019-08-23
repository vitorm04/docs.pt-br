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
ms.openlocfilehash: f323e91e60c9735a51e955eaab6673ca167f294d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951872"
---
# <a name="imetadataimportresolvetyperef-method"></a><span data-ttu-id="82dc5-102">Método IMetaDataImport::ResolveTypeRef</span><span class="sxs-lookup"><span data-stu-id="82dc5-102">IMetaDataImport::ResolveTypeRef Method</span></span>
<span data-ttu-id="82dc5-103">Resolve uma <xref:System.Type> referência representada pelo token TypeRef especificado.</span><span class="sxs-lookup"><span data-stu-id="82dc5-103">Resolves a <xref:System.Type> reference represented by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82dc5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="82dc5-104">Syntax</span></span>  
  
```cpp  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82dc5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="82dc5-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="82dc5-106">no O token de metadados TypeRef para retornar as informações de tipo referenciadas.</span><span class="sxs-lookup"><span data-stu-id="82dc5-106">[in] The TypeRef metadata token to return the referenced type information for.</span></span>  
  
 `riid`  
 <span data-ttu-id="82dc5-107">no O IID da interface a ser retornada `ppIScope`.</span><span class="sxs-lookup"><span data-stu-id="82dc5-107">[in] The IID of the interface to return in `ppIScope`.</span></span> <span data-ttu-id="82dc5-108">Normalmente, isso seria IID_IMetaDataImport.</span><span class="sxs-lookup"><span data-stu-id="82dc5-108">Typically, this would be IID_IMetaDataImport.</span></span>  
  
 `ppIScope`  
 <span data-ttu-id="82dc5-109">fora Uma interface para o escopo do módulo no qual o tipo referenciado é definido.</span><span class="sxs-lookup"><span data-stu-id="82dc5-109">[out] An interface to the module scope in which the referenced type is defined.</span></span>  
  
 `ptd`  
 <span data-ttu-id="82dc5-110">fora Um ponteiro para um token de TypeDef que representa o tipo referenciado.</span><span class="sxs-lookup"><span data-stu-id="82dc5-110">[out] A pointer to a TypeDef token that represents the referenced type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82dc5-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="82dc5-111">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="82dc5-112">Não use esse método se vários domínios de aplicativo forem carregados.</span><span class="sxs-lookup"><span data-stu-id="82dc5-112">Do not use this method if multiple application domains are loaded.</span></span> <span data-ttu-id="82dc5-113">O método não respeita os limites do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="82dc5-113">The method does not respect application domain boundaries.</span></span> <span data-ttu-id="82dc5-114">Se várias versões de um assembly forem carregadas e contiverem o mesmo tipo com o mesmo namespace, o método retornará o escopo do módulo do primeiro tipo que encontrar.</span><span class="sxs-lookup"><span data-stu-id="82dc5-114">If multiple versions of an assembly are loaded, and they contain the same type with the same namespace, the method returns the module scope of the first type it finds.</span></span>  
  
 <span data-ttu-id="82dc5-115">O `ResolveTypeRef` método procura a definição de tipo em outros módulos.</span><span class="sxs-lookup"><span data-stu-id="82dc5-115">The `ResolveTypeRef` method searches for the type definition in other modules.</span></span> <span data-ttu-id="82dc5-116">Se a definição de tipo for encontrada `ResolveTypeRef` , retorna uma interface para esse escopo de módulo, bem como o token de typedef para o tipo.</span><span class="sxs-lookup"><span data-stu-id="82dc5-116">If the type definition is found, `ResolveTypeRef` returns an interface to that module scope as well as the TypeDef token for the type.</span></span>  
  
 <span data-ttu-id="82dc5-117">Se a referência de tipo a ser resolvida tiver um escopo de resolução de `ResolveTypeRef` AssemblyRef, o método procurará uma correspondência somente nos escopos de metadados que já foram abertos com chamadas para o método [IMetaDataDispenser:: OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) ou o [ Método IMetaDataDispenser:: OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) .</span><span class="sxs-lookup"><span data-stu-id="82dc5-117">If the type reference to be resolved has a resolution scope of AssemblyRef, the `ResolveTypeRef` method searches for a match only in the metadata scopes that have already been opened with calls to either the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method or the [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method.</span></span> <span data-ttu-id="82dc5-118">Isso ocorre porque `ResolveTypeRef` o não pode determinar apenas o escopo de AssemblyRef em que no disco ou no cache de assembly global o assembly está armazenado.</span><span class="sxs-lookup"><span data-stu-id="82dc5-118">This is because `ResolveTypeRef` cannot determine from only the AssemblyRef scope where on disk or in the global assembly cache the assembly is stored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82dc5-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="82dc5-119">Requirements</span></span>  
 <span data-ttu-id="82dc5-120">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82dc5-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82dc5-121">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="82dc5-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="82dc5-122">**Biblioteca** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="82dc5-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="82dc5-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82dc5-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82dc5-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82dc5-124">See also</span></span>

- [<span data-ttu-id="82dc5-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="82dc5-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="82dc5-126">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="82dc5-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
