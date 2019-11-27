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
ms.openlocfilehash: ed193aab8beb0de1321aa1d52ec9f963b08b316c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441669"
---
# <a name="imetadataimportenummemberswithname-method"></a><span data-ttu-id="f3eb2-102">Método IMetaDataImport::EnumMembersWithName</span><span class="sxs-lookup"><span data-stu-id="f3eb2-102">IMetaDataImport::EnumMembersWithName Method</span></span>
<span data-ttu-id="f3eb2-103">Enumera os tokens MemberDef que representam os membros do tipo especificado com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="f3eb2-103">Enumerates MemberDef tokens representing members of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3eb2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f3eb2-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="f3eb2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f3eb2-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="f3eb2-106">[entrada, saída] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="f3eb2-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="f3eb2-107">no Um token de TypeDef que representa o tipo com membros a serem enumerados.</span><span class="sxs-lookup"><span data-stu-id="f3eb2-107">[in] A TypeDef token representing the type with members to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="f3eb2-108">no O nome do membro que limita o escopo do enumerador.</span><span class="sxs-lookup"><span data-stu-id="f3eb2-108">[in] The member name that limits the scope of the enumerator.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="f3eb2-109">fora A matriz usada para armazenar os tokens MemberDef.</span><span class="sxs-lookup"><span data-stu-id="f3eb2-109">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f3eb2-110">no O tamanho máximo da matriz de `rMembers`.</span><span class="sxs-lookup"><span data-stu-id="f3eb2-110">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="f3eb2-111">fora O número real de tokens MemberDef retornados em `rMembers`.</span><span class="sxs-lookup"><span data-stu-id="f3eb2-111">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3eb2-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="f3eb2-112">Remarks</span></span>  
 <span data-ttu-id="f3eb2-113">Esse método enumera campos e métodos, mas não propriedades ou eventos.</span><span class="sxs-lookup"><span data-stu-id="f3eb2-113">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="f3eb2-114">Ao contrário de [IMetaDataImport:: EnumMembers](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md), `EnumMembersWithName` descarta todos os tokens de campo e membro que não têm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="f3eb2-114">Unlike [IMetaDataImport::EnumMembers](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md), `EnumMembersWithName` discards all field and member tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f3eb2-115">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="f3eb2-115">Return Value</span></span>  
  
|<span data-ttu-id="f3eb2-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f3eb2-116">HRESULT</span></span>|<span data-ttu-id="f3eb2-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="f3eb2-117">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f3eb2-118">`EnumTypeDefs` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="f3eb2-118">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f3eb2-119">Não há tokens MemberDef para enumerar.</span><span class="sxs-lookup"><span data-stu-id="f3eb2-119">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="f3eb2-120">Nesse caso, `pcTokens` é zero.</span><span class="sxs-lookup"><span data-stu-id="f3eb2-120">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f3eb2-121">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="f3eb2-121">Requirements</span></span>  
 <span data-ttu-id="f3eb2-122">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3eb2-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3eb2-123">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f3eb2-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f3eb2-124">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f3eb2-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f3eb2-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3eb2-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3eb2-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3eb2-126">See also</span></span>

- [<span data-ttu-id="f3eb2-127">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="f3eb2-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="f3eb2-128">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="f3eb2-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
