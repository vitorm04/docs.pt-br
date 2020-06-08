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
ms.openlocfilehash: ea451bdd645d2d4dea4c5dd00408e0bc51804803
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492035"
---
# <a name="imetadataimportenummemberswithname-method"></a><span data-ttu-id="8c98e-102">Método IMetaDataImport::EnumMembersWithName</span><span class="sxs-lookup"><span data-stu-id="8c98e-102">IMetaDataImport::EnumMembersWithName Method</span></span>
<span data-ttu-id="8c98e-103">Enumera os tokens MemberDef que representam os membros do tipo especificado com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="8c98e-103">Enumerates MemberDef tokens representing members of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c98e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8c98e-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMembersWithName (  
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   cl,
   [in]      LPCWSTR     szName,
   [out]     mdToken     rMembers[],
   [in]      ULONG       cMax,
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c98e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8c98e-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="8c98e-106">[entrada, saída] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="8c98e-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="8c98e-107">no Um token de TypeDef que representa o tipo com membros a serem enumerados.</span><span class="sxs-lookup"><span data-stu-id="8c98e-107">[in] A TypeDef token representing the type with members to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="8c98e-108">no O nome do membro que limita o escopo do enumerador.</span><span class="sxs-lookup"><span data-stu-id="8c98e-108">[in] The member name that limits the scope of the enumerator.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="8c98e-109">fora A matriz usada para armazenar os tokens MemberDef.</span><span class="sxs-lookup"><span data-stu-id="8c98e-109">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="8c98e-110">no O tamanho máximo da `rMembers` matriz.</span><span class="sxs-lookup"><span data-stu-id="8c98e-110">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="8c98e-111">fora O número real de tokens MemberDef retornados em `rMembers` .</span><span class="sxs-lookup"><span data-stu-id="8c98e-111">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c98e-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="8c98e-112">Remarks</span></span>  
 <span data-ttu-id="8c98e-113">Esse método enumera campos e métodos, mas não propriedades ou eventos.</span><span class="sxs-lookup"><span data-stu-id="8c98e-113">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="8c98e-114">Ao contrário de [IMetaDataImport:: EnumMembers](imetadataimport-enummembers-method.md), `EnumMembersWithName` descarta todos os tokens de campo e membro que não têm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="8c98e-114">Unlike [IMetaDataImport::EnumMembers](imetadataimport-enummembers-method.md), `EnumMembersWithName` discards all field and member tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c98e-115">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="8c98e-115">Return Value</span></span>  
  
|<span data-ttu-id="8c98e-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8c98e-116">HRESULT</span></span>|<span data-ttu-id="8c98e-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="8c98e-117">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="8c98e-118">`EnumTypeDefs`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="8c98e-118">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="8c98e-119">Não há tokens MemberDef para enumerar.</span><span class="sxs-lookup"><span data-stu-id="8c98e-119">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="8c98e-120">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="8c98e-120">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8c98e-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8c98e-121">Requirements</span></span>  
 <span data-ttu-id="8c98e-122">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c98e-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c98e-123">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8c98e-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8c98e-124">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8c98e-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8c98e-125">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c98e-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c98e-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="8c98e-126">See also</span></span>

- [<span data-ttu-id="8c98e-127">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="8c98e-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="8c98e-128">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="8c98e-128">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
