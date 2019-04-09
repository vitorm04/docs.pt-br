---
title: Método IMetaDataImport::EnumMembersWithName
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMembersWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembersWithName
helpviewer_keywords:
- IMetaDataImport::EnumMembersWithName method [.NET Framework metadata]
- EnumMembersWithName method [.NET Framework metadata]
ms.assetid: 7c9e9120-3104-42f0-86ce-19a025f20dcc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c2509945d2799b81e036888d146a51cee87fda09
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169839"
---
# <a name="imetadataimportenummemberswithname-method"></a><span data-ttu-id="ac3f8-102">Método IMetaDataImport::EnumMembersWithName</span><span class="sxs-lookup"><span data-stu-id="ac3f8-102">IMetaDataImport::EnumMembersWithName Method</span></span>
<span data-ttu-id="ac3f8-103">Enumera os tokens de MemberDef que representa os membros do tipo especificado com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="ac3f8-103">Enumerates MemberDef tokens representing members of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac3f8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac3f8-104">Syntax</span></span>  
  
```  
HRESULT EnumMembersWithName (  
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   cl,   
   [in]      LPCWSTR     szName,   
   [out]     mdToken     rMembers[],   
   [in]      ULONG       cMax,   
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac3f8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ac3f8-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="ac3f8-106">[no, out] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="ac3f8-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="ac3f8-107">[in] Um token de TypeDef que representa o tipo com membros para enumerar.</span><span class="sxs-lookup"><span data-stu-id="ac3f8-107">[in] A TypeDef token representing the type with members to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="ac3f8-108">[in] O nome do membro que limita o escopo do enumerador.</span><span class="sxs-lookup"><span data-stu-id="ac3f8-108">[in] The member name that limits the scope of the enumerator.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="ac3f8-109">[out] A matriz usada para armazenar os tokens de MemberDef.</span><span class="sxs-lookup"><span data-stu-id="ac3f8-109">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="ac3f8-110">[in] O tamanho máximo da `rMembers` matriz.</span><span class="sxs-lookup"><span data-stu-id="ac3f8-110">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="ac3f8-111">[out] O número real de tokens MemberDef retornado no `rMembers`.</span><span class="sxs-lookup"><span data-stu-id="ac3f8-111">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac3f8-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="ac3f8-112">Remarks</span></span>  
 <span data-ttu-id="ac3f8-113">Esse método enumera os campos e métodos, mas não as propriedades ou eventos.</span><span class="sxs-lookup"><span data-stu-id="ac3f8-113">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="ac3f8-114">Diferentemente [imetadataimport:: Enummembers](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md), `EnumMembersWithName` descarta todos os tokens de campo e o membro que não têm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="ac3f8-114">Unlike [IMetaDataImport::EnumMembers](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md), `EnumMembersWithName` discards all field and member tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac3f8-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ac3f8-115">Return Value</span></span>  
  
|<span data-ttu-id="ac3f8-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ac3f8-116">HRESULT</span></span>|<span data-ttu-id="ac3f8-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac3f8-117">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumTypeDefs` <span data-ttu-id="ac3f8-118">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="ac3f8-118">returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="ac3f8-119">Não há nenhum token MemberDef para enumerar.</span><span class="sxs-lookup"><span data-stu-id="ac3f8-119">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="ac3f8-120">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="ac3f8-120">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ac3f8-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ac3f8-121">Requirements</span></span>  
 <span data-ttu-id="ac3f8-122">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac3f8-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac3f8-123">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ac3f8-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ac3f8-124">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="ac3f8-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="ac3f8-125">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="ac3f8-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ac3f8-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac3f8-126">See also</span></span>

- [<span data-ttu-id="ac3f8-127">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="ac3f8-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="ac3f8-128">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="ac3f8-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
