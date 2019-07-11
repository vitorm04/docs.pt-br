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
ms.openlocfilehash: 50035799fcfa4c4b08404d63fe91e7dba85722fa
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758837"
---
# <a name="imetadataimportenummembers-method"></a><span data-ttu-id="44f68-102">Método IMetaDataImport::EnumMembers</span><span class="sxs-lookup"><span data-stu-id="44f68-102">IMetaDataImport::EnumMembers Method</span></span>
<span data-ttu-id="44f68-103">Enumera os tokens de MemberDef que representa os membros do tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="44f68-103">Enumerates MemberDef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44f68-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="44f68-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMembers (   
   [in, out]  HCORENUM    *phEnum,   
   [in]  mdTypeDef   cl,   
   [out] mdToken     rMembers[],   
   [in]  ULONG       cMax,   
   [out] ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44f68-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="44f68-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="44f68-106">[no, out] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="44f68-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="44f68-107">[in] Um token de TypeDef que representa o tipo cujos membros são a serem enumerados.</span><span class="sxs-lookup"><span data-stu-id="44f68-107">[in] A TypeDef token representing the type whose members are to be enumerated.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="44f68-108">[out] A matriz usada para manter os tokens de MemberDef.</span><span class="sxs-lookup"><span data-stu-id="44f68-108">[out] The array used to hold the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="44f68-109">[in] O tamanho máximo da `rMembers` matriz.</span><span class="sxs-lookup"><span data-stu-id="44f68-109">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="44f68-110">[out] O número real de tokens MemberDef retornado no `rMembers`.</span><span class="sxs-lookup"><span data-stu-id="44f68-110">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44f68-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="44f68-111">Return Value</span></span>  
  
|<span data-ttu-id="44f68-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="44f68-112">HRESULT</span></span>|<span data-ttu-id="44f68-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="44f68-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="44f68-114">`EnumMembers` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="44f68-114">`EnumMembers` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="44f68-115">Não há nenhum token MemberDef para enumerar.</span><span class="sxs-lookup"><span data-stu-id="44f68-115">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="44f68-116">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="44f68-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44f68-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="44f68-117">Remarks</span></span>  
 <span data-ttu-id="44f68-118">Quando enumerando coleções de membros de uma classe `EnumMembers` retorna somente os membros (campos e métodos, mas **não** propriedades ou eventos) definidos diretamente na classe.</span><span class="sxs-lookup"><span data-stu-id="44f68-118">When enumerating collections of members for a class, `EnumMembers` returns only members (fields and methods, but **not** properties or events) defined directly on the class.</span></span> <span data-ttu-id="44f68-119">Ele não retorna todos os membros que herda a classe, mesmo se a classe fornece uma implementação para esses membros herdados.</span><span class="sxs-lookup"><span data-stu-id="44f68-119">It does not return any members that the class inherits, even if the class provides an implementation for those inherited members.</span></span> <span data-ttu-id="44f68-120">Para enumerar os membros herdados, o chamador deve movimentar explicitamente a cadeia de herança.</span><span class="sxs-lookup"><span data-stu-id="44f68-120">To enumerate inherited members, the caller must explicitly walk the inheritance chain.</span></span> <span data-ttu-id="44f68-121">Observe que as regras para a cadeia de herança podem variar dependendo do idioma ou o compilador que se emitiu os metadados originais.</span><span class="sxs-lookup"><span data-stu-id="44f68-121">Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.</span></span>
 
 <span data-ttu-id="44f68-122">Propriedades e eventos não são enumerados pelo `EnumMembers`.</span><span class="sxs-lookup"><span data-stu-id="44f68-122">Properties and events are not enumerated by `EnumMembers`.</span></span> <span data-ttu-id="44f68-123">Para enumerar os, use [EnumProperties](imetadataimport-enumproperties-method.md) ou [EnumEvents](imetadataimport-enumevents-method.md).</span><span class="sxs-lookup"><span data-stu-id="44f68-123">To enumerate those, use [EnumProperties](imetadataimport-enumproperties-method.md) or [EnumEvents](imetadataimport-enumevents-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="44f68-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="44f68-124">Requirements</span></span>  
 <span data-ttu-id="44f68-125">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44f68-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44f68-126">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="44f68-126">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="44f68-127">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="44f68-127">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="44f68-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44f68-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44f68-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44f68-129">See also</span></span>

- [<span data-ttu-id="44f68-130">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="44f68-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="44f68-131">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="44f68-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
