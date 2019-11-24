---
title: Método IMetaDataImport::EnumSignatures
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumSignatures
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumSignatures
helpviewer_keywords:
- EnumSignatures method [.NET Framework metadata]
- IMetaDataImport::EnumSignatures method [.NET Framework metadata]
ms.assetid: d0d65060-6f90-42a2-95cf-6ffb04352996
topic_type:
- apiref
ms.openlocfilehash: 9dbbdcc9d0fb9f0a8d2a64edfa4a0ad92570933c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450012"
---
# <a name="imetadataimportenumsignatures-method"></a><span data-ttu-id="64588-102">Método IMetaDataImport::EnumSignatures</span><span class="sxs-lookup"><span data-stu-id="64588-102">IMetaDataImport::EnumSignatures Method</span></span>
<span data-ttu-id="64588-103">Enumerates Signature tokens representing stand-alone signatures in the current scope.</span><span class="sxs-lookup"><span data-stu-id="64588-103">Enumerates Signature tokens representing stand-alone signatures in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64588-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="64588-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumSignatures (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdSignature  rSignatures[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcSignatures  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64588-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="64588-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="64588-106">[in, out] A pointer to the enumerator.</span><span class="sxs-lookup"><span data-stu-id="64588-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="64588-107">This must be NULL for the first call of this method.</span><span class="sxs-lookup"><span data-stu-id="64588-107">This must be NULL for the first call of this method.</span></span>  
  
 `rSignatures`  
 <span data-ttu-id="64588-108">[out] The array used to store the Signature tokens.</span><span class="sxs-lookup"><span data-stu-id="64588-108">[out] The array used to store the Signature tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="64588-109">[in] The maximum size of the `rSignatures` array.</span><span class="sxs-lookup"><span data-stu-id="64588-109">[in] The maximum size of the `rSignatures` array.</span></span>  
  
 `pcSignatures`  
 <span data-ttu-id="64588-110">[out] The number of Signature tokens returned in `rSignatures`.</span><span class="sxs-lookup"><span data-stu-id="64588-110">[out] The number of Signature tokens returned in `rSignatures`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="64588-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="64588-111">Return Value</span></span>  
  
|<span data-ttu-id="64588-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="64588-112">HRESULT</span></span>|<span data-ttu-id="64588-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="64588-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="64588-114">`EnumSignatures` returned successfully.</span><span class="sxs-lookup"><span data-stu-id="64588-114">`EnumSignatures` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="64588-115">There are no tokens to enumerate.</span><span class="sxs-lookup"><span data-stu-id="64588-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="64588-116">In that case, `pcSignatures` is zero.</span><span class="sxs-lookup"><span data-stu-id="64588-116">In that case, `pcSignatures` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64588-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="64588-117">Remarks</span></span>  
 <span data-ttu-id="64588-118">The Signature tokens are created by the [IMetaDataEmit::GetTokenFromSig](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="64588-118">The Signature tokens are created by the [IMetaDataEmit::GetTokenFromSig](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64588-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="64588-119">Requirements</span></span>  
 <span data-ttu-id="64588-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64588-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64588-121">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="64588-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="64588-122">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="64588-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="64588-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64588-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64588-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64588-124">See also</span></span>

- [<span data-ttu-id="64588-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="64588-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="64588-126">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="64588-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
