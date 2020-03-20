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
ms.openlocfilehash: 20c7a90f27defa18a5ef311d1f3a549b81fc5c40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175480"
---
# <a name="imetadataimportenummembers-method"></a><span data-ttu-id="b96ce-102">Método IMetaDataImport::EnumMembers</span><span class="sxs-lookup"><span data-stu-id="b96ce-102">IMetaDataImport::EnumMembers Method</span></span>
<span data-ttu-id="b96ce-103">Enumera os tokens MemberDef representando membros do tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="b96ce-103">Enumerates MemberDef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b96ce-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b96ce-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMembers (
   [in, out]  HCORENUM    *phEnum,
   [in]  mdTypeDef   cl,
   [out] mdToken     rMembers[],
   [in]  ULONG       cMax,
   [out] ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b96ce-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="b96ce-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="b96ce-106">[dentro, fora] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="b96ce-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="b96ce-107">[em] Um token TypeDef representando o tipo cujos membros devem ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="b96ce-107">[in] A TypeDef token representing the type whose members are to be enumerated.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="b96ce-108">[fora] A matriz usada para conter os tokens MemberDef.</span><span class="sxs-lookup"><span data-stu-id="b96ce-108">[out] The array used to hold the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b96ce-109">[em] O tamanho máximo `rMembers` da matriz.</span><span class="sxs-lookup"><span data-stu-id="b96ce-109">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="b96ce-110">[fora] O número real de tokens MemberDef retornou em `rMembers`.</span><span class="sxs-lookup"><span data-stu-id="b96ce-110">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b96ce-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b96ce-111">Return Value</span></span>  
  
|<span data-ttu-id="b96ce-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b96ce-112">HRESULT</span></span>|<span data-ttu-id="b96ce-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="b96ce-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b96ce-114">`EnumMembers`retornou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="b96ce-114">`EnumMembers` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b96ce-115">Não há tokens MemberDef para enumerar.</span><span class="sxs-lookup"><span data-stu-id="b96ce-115">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="b96ce-116">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="b96ce-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b96ce-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="b96ce-117">Remarks</span></span>  
 <span data-ttu-id="b96ce-118">Ao enumerar coleções de membros `EnumMembers` para uma classe, retorna apenas membros (campos e métodos, mas **não** propriedades ou eventos) definidos diretamente na classe.</span><span class="sxs-lookup"><span data-stu-id="b96ce-118">When enumerating collections of members for a class, `EnumMembers` returns only members (fields and methods, but **not** properties or events) defined directly on the class.</span></span> <span data-ttu-id="b96ce-119">Não devolve nenhum membro que a classe herde, mesmo que a classe forneça uma implementação para os membros herdados.</span><span class="sxs-lookup"><span data-stu-id="b96ce-119">It does not return any members that the class inherits, even if the class provides an implementation for those inherited members.</span></span> <span data-ttu-id="b96ce-120">Para enumerar os membros herdados, o interlocutor deve andar explicitamente na cadeia de herança.</span><span class="sxs-lookup"><span data-stu-id="b96ce-120">To enumerate inherited members, the caller must explicitly walk the inheritance chain.</span></span> <span data-ttu-id="b96ce-121">Observe que as regras para a cadeia de herança podem variar dependendo do idioma ou compilador que emitia os metadados originais.</span><span class="sxs-lookup"><span data-stu-id="b96ce-121">Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.</span></span>

 <span data-ttu-id="b96ce-122">Propriedades e eventos não são `EnumMembers`enumerados por .</span><span class="sxs-lookup"><span data-stu-id="b96ce-122">Properties and events are not enumerated by `EnumMembers`.</span></span> <span data-ttu-id="b96ce-123">Para enumerar esses, use [EnumProperties](imetadataimport-enumproperties-method.md) ou [EnumEvents](imetadataimport-enumevents-method.md).</span><span class="sxs-lookup"><span data-stu-id="b96ce-123">To enumerate those, use [EnumProperties](imetadataimport-enumproperties-method.md) or [EnumEvents](imetadataimport-enumevents-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="b96ce-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b96ce-124">Requirements</span></span>  
 <span data-ttu-id="b96ce-125">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b96ce-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b96ce-126">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b96ce-126">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b96ce-127">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b96ce-127">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b96ce-128">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b96ce-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b96ce-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="b96ce-129">See also</span></span>

- [<span data-ttu-id="b96ce-130">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="b96ce-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b96ce-131">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="b96ce-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
