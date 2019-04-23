---
title: Método IMetaDataImport::EnumMembers
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMembers
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembers
helpviewer_keywords:
- IMetaDataImport::EnumMembers method [.NET Framework metadata]
- EnumMembers method [.NET Framework metadata]
ms.assetid: 3fb8e178-342b-4c89-9bcf-f7f834e6cb77
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e8d871f2ecbd96d5bda781b2ae11b94efd409442
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59128395"
---
# <a name="imetadataimportenummembers-method"></a><span data-ttu-id="147dd-102">Método IMetaDataImport::EnumMembers</span><span class="sxs-lookup"><span data-stu-id="147dd-102">IMetaDataImport::EnumMembers Method</span></span>
<span data-ttu-id="147dd-103">Enumera os tokens de MemberDef que representa os membros do tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="147dd-103">Enumerates MemberDef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="147dd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="147dd-104">Syntax</span></span>  
  
```  
HRESULT EnumMembers (   
   [in, out]  HCORENUM    *phEnum,   
   [in]  mdTypeDef   cl,   
   [out] mdToken     rMembers[],   
   [in]  ULONG       cMax,   
   [out] ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="147dd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="147dd-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="147dd-106">[no, out] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="147dd-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="147dd-107">[in] Um token de TypeDef que representa o tipo cujos membros são a serem enumerados.</span><span class="sxs-lookup"><span data-stu-id="147dd-107">[in] A TypeDef token representing the type whose members are to be enumerated.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="147dd-108">[out] A matriz usada para manter os tokens de MemberDef.</span><span class="sxs-lookup"><span data-stu-id="147dd-108">[out] The array used to hold the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="147dd-109">[in] O tamanho máximo da `rMembers` matriz.</span><span class="sxs-lookup"><span data-stu-id="147dd-109">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="147dd-110">[out] O número real de tokens MemberDef retornado no `rMembers`.</span><span class="sxs-lookup"><span data-stu-id="147dd-110">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="147dd-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="147dd-111">Return Value</span></span>  
  
|<span data-ttu-id="147dd-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="147dd-112">HRESULT</span></span>|<span data-ttu-id="147dd-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="147dd-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="147dd-114">`EnumMembers` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="147dd-114">`EnumMembers` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="147dd-115">Não há nenhum token MemberDef para enumerar.</span><span class="sxs-lookup"><span data-stu-id="147dd-115">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="147dd-116">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="147dd-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="147dd-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="147dd-117">Remarks</span></span>  
 <span data-ttu-id="147dd-118">Quando enumerando coleções de membros de uma classe `EnumMembers` retorna somente os membros (campos e métodos, mas **não** propriedades ou eventos) definidos diretamente na classe.</span><span class="sxs-lookup"><span data-stu-id="147dd-118">When enumerating collections of members for a class, `EnumMembers` returns only members (fields and methods, but **not** properties or events) defined directly on the class.</span></span> <span data-ttu-id="147dd-119">Ele não retorna todos os membros que herda a classe, mesmo se a classe fornece uma implementação para esses membros herdados.</span><span class="sxs-lookup"><span data-stu-id="147dd-119">It does not return any members that the class inherits, even if the class provides an implementation for those inherited members.</span></span> <span data-ttu-id="147dd-120">Para enumerar os membros herdados, o chamador deve movimentar explicitamente a cadeia de herança.</span><span class="sxs-lookup"><span data-stu-id="147dd-120">To enumerate inherited members, the caller must explicitly walk the inheritance chain.</span></span> <span data-ttu-id="147dd-121">Observe que as regras para a cadeia de herança podem variar dependendo do idioma ou o compilador que se emitiu os metadados originais.</span><span class="sxs-lookup"><span data-stu-id="147dd-121">Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.</span></span>
 
 <span data-ttu-id="147dd-122">Propriedades e eventos não são enumerados pelo `EnumMembers`.</span><span class="sxs-lookup"><span data-stu-id="147dd-122">Properties and events are not enumerated by `EnumMembers`.</span></span> <span data-ttu-id="147dd-123">Para enumerar os, use [EnumProperties](imetadataimport-enumproperties-method.md) ou [EnumEvents](imetadataimport-enumevents-method.md).</span><span class="sxs-lookup"><span data-stu-id="147dd-123">To enumerate those, use [EnumProperties](imetadataimport-enumproperties-method.md) or [EnumEvents](imetadataimport-enumevents-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="147dd-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="147dd-124">Requirements</span></span>  
 <span data-ttu-id="147dd-125">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="147dd-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="147dd-126">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="147dd-126">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="147dd-127">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="147dd-127">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="147dd-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="147dd-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="147dd-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="147dd-129">See also</span></span>

- [<span data-ttu-id="147dd-130">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="147dd-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="147dd-131">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="147dd-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
