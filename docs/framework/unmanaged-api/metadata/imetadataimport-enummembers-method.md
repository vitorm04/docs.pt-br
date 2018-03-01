---
title: "Método IMetaDataImport::EnumMembers"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: aa7dabad0e555fe965cba4e5cbc69c10c9826b8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenummembers-method"></a><span data-ttu-id="61d00-102">Método IMetaDataImport::EnumMembers</span><span class="sxs-lookup"><span data-stu-id="61d00-102">IMetaDataImport::EnumMembers Method</span></span>
<span data-ttu-id="61d00-103">Enumera os tokens de MemberDef que representa os membros do tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="61d00-103">Enumerates MemberDef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61d00-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="61d00-104">Syntax</span></span>  
  
```  
HRESULT EnumMembers (   
   [in, out]  HCORENUM    *phEnum,   
   [in]  mdTypeDef   cl,   
   [out] mdToken     rMembers[],   
   [in]  ULONG       cMax,   
   [out] ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="61d00-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="61d00-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="61d00-106">[out no] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="61d00-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="61d00-107">[in] Um token de TypeDef que representa o tipo cujos membros são a serem enumerados.</span><span class="sxs-lookup"><span data-stu-id="61d00-107">[in] A TypeDef token representing the type whose members are to be enumerated.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="61d00-108">[out] A matriz usada para manter os tokens de MemberDef.</span><span class="sxs-lookup"><span data-stu-id="61d00-108">[out] The array used to hold the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="61d00-109">[in] O tamanho máximo da `rMembers` matriz.</span><span class="sxs-lookup"><span data-stu-id="61d00-109">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="61d00-110">[out] O número real de tokens MemberDef retornado em `rMembers`.</span><span class="sxs-lookup"><span data-stu-id="61d00-110">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="61d00-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="61d00-111">Return Value</span></span>  
  
|<span data-ttu-id="61d00-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="61d00-112">HRESULT</span></span>|<span data-ttu-id="61d00-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="61d00-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="61d00-114">`EnumMembers`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="61d00-114">`EnumMembers` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="61d00-115">Não há nenhum token MemberDef enumerar.</span><span class="sxs-lookup"><span data-stu-id="61d00-115">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="61d00-116">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="61d00-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61d00-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="61d00-117">Remarks</span></span>  
 <span data-ttu-id="61d00-118">Quando enumerando coleções de membros de uma classe, `EnumMembers` retorna somente os membros definidos diretamente na classe.</span><span class="sxs-lookup"><span data-stu-id="61d00-118">When enumerating collections of members for a class, `EnumMembers` returns only members defined directly on the class.</span></span> <span data-ttu-id="61d00-119">Ele não retorna todos os membros de classe herdada, mesmo se a classe fornece uma implementação para esses membros herdados.</span><span class="sxs-lookup"><span data-stu-id="61d00-119">It does not return any members that the class inherits, even if the class provides an implementation for those inherited members.</span></span> <span data-ttu-id="61d00-120">Para enumerar os membros herdados, o chamador deve percorrer explicitamente a cadeia de herança.</span><span class="sxs-lookup"><span data-stu-id="61d00-120">To enumerate inherited members, the caller must explicitly walk the inheritance chain.</span></span> <span data-ttu-id="61d00-121">Observe que as regras para a cadeia de herança podem variar dependendo do idioma ou o compilador que emitiu os metadados originais.</span><span class="sxs-lookup"><span data-stu-id="61d00-121">Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61d00-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="61d00-122">Requirements</span></span>  
 <span data-ttu-id="61d00-123">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61d00-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61d00-124">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="61d00-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="61d00-125">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="61d00-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="61d00-126">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61d00-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61d00-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61d00-127">See Also</span></span>  
 [<span data-ttu-id="61d00-128">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="61d00-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="61d00-129">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="61d00-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
