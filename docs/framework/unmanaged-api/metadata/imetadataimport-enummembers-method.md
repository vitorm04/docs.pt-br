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
ms.openlocfilehash: acb772a64c8f13405f2836bb5f4f308986dce414
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447661"
---
# <a name="imetadataimportenummembers-method"></a><span data-ttu-id="5f0b7-102">Método IMetaDataImport::EnumMembers</span><span class="sxs-lookup"><span data-stu-id="5f0b7-102">IMetaDataImport::EnumMembers Method</span></span>
<span data-ttu-id="5f0b7-103">Enumera os tokens MemberDef que representam os membros do tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="5f0b7-103">Enumerates MemberDef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f0b7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5f0b7-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMembers (   
   [in, out]  HCORENUM    *phEnum,   
   [in]  mdTypeDef   cl,   
   [out] mdToken     rMembers[],   
   [in]  ULONG       cMax,   
   [out] ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f0b7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5f0b7-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="5f0b7-106">[entrada, saída] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="5f0b7-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="5f0b7-107">no Um token de TypeDef que representa o tipo cujos membros devem ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="5f0b7-107">[in] A TypeDef token representing the type whose members are to be enumerated.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="5f0b7-108">fora A matriz usada para manter os tokens MemberDef.</span><span class="sxs-lookup"><span data-stu-id="5f0b7-108">[out] The array used to hold the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="5f0b7-109">no O tamanho máximo da matriz de `rMembers`.</span><span class="sxs-lookup"><span data-stu-id="5f0b7-109">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="5f0b7-110">fora O número real de tokens MemberDef retornados em `rMembers`.</span><span class="sxs-lookup"><span data-stu-id="5f0b7-110">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5f0b7-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="5f0b7-111">Return Value</span></span>  
  
|<span data-ttu-id="5f0b7-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5f0b7-112">HRESULT</span></span>|<span data-ttu-id="5f0b7-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="5f0b7-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="5f0b7-114">`EnumMembers` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="5f0b7-114">`EnumMembers` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="5f0b7-115">Não há tokens MemberDef para enumerar.</span><span class="sxs-lookup"><span data-stu-id="5f0b7-115">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="5f0b7-116">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="5f0b7-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f0b7-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="5f0b7-117">Remarks</span></span>  
 <span data-ttu-id="5f0b7-118">Ao enumerar coleções de membros para uma classe, `EnumMembers` retorna somente Membros (campos e métodos, mas **não** Propriedades ou eventos) definidos diretamente na classe.</span><span class="sxs-lookup"><span data-stu-id="5f0b7-118">When enumerating collections of members for a class, `EnumMembers` returns only members (fields and methods, but **not** properties or events) defined directly on the class.</span></span> <span data-ttu-id="5f0b7-119">Ele não retorna nenhum membro herdado pela classe, mesmo que a classe forneça uma implementação para esses membros herdados.</span><span class="sxs-lookup"><span data-stu-id="5f0b7-119">It does not return any members that the class inherits, even if the class provides an implementation for those inherited members.</span></span> <span data-ttu-id="5f0b7-120">Para enumerar membros herdados, o chamador deve percorrer a cadeia de herança explicitamente.</span><span class="sxs-lookup"><span data-stu-id="5f0b7-120">To enumerate inherited members, the caller must explicitly walk the inheritance chain.</span></span> <span data-ttu-id="5f0b7-121">Observe que as regras para a cadeia de herança podem variar dependendo do idioma ou do compilador que emitiu os metadados originais.</span><span class="sxs-lookup"><span data-stu-id="5f0b7-121">Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.</span></span>
 
 <span data-ttu-id="5f0b7-122">As propriedades e os eventos não são enumerados por `EnumMembers`.</span><span class="sxs-lookup"><span data-stu-id="5f0b7-122">Properties and events are not enumerated by `EnumMembers`.</span></span> <span data-ttu-id="5f0b7-123">Para enumerar, use [EnumProperties](imetadataimport-enumproperties-method.md) ou [EnumEvents](imetadataimport-enumevents-method.md).</span><span class="sxs-lookup"><span data-stu-id="5f0b7-123">To enumerate those, use [EnumProperties](imetadataimport-enumproperties-method.md) or [EnumEvents](imetadataimport-enumevents-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="5f0b7-124">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="5f0b7-124">Requirements</span></span>  
 <span data-ttu-id="5f0b7-125">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f0b7-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f0b7-126">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5f0b7-126">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5f0b7-127">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5f0b7-127">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5f0b7-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f0b7-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f0b7-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5f0b7-129">See also</span></span>

- [<span data-ttu-id="5f0b7-130">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="5f0b7-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="5f0b7-131">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="5f0b7-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
