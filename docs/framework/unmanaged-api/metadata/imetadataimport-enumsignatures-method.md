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
ms.openlocfilehash: 652ebf1be6a58e08da27aaed5b2e84a8f2aee98a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503764"
---
# <a name="imetadataimportenumsignatures-method"></a><span data-ttu-id="bffe1-102">Método IMetaDataImport::EnumSignatures</span><span class="sxs-lookup"><span data-stu-id="bffe1-102">IMetaDataImport::EnumSignatures Method</span></span>
<span data-ttu-id="bffe1-103">Enumera os tokens de assinatura que representam assinaturas autônomas no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="bffe1-103">Enumerates Signature tokens representing stand-alone signatures in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bffe1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bffe1-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumSignatures (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdSignature  rSignatures[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcSignatures  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bffe1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bffe1-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="bffe1-106">[entrada, saída] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="bffe1-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="bffe1-107">Isso deve ser nulo para a primeira chamada deste método.</span><span class="sxs-lookup"><span data-stu-id="bffe1-107">This must be NULL for the first call of this method.</span></span>  
  
 `rSignatures`  
 <span data-ttu-id="bffe1-108">fora A matriz usada para armazenar os tokens de assinatura.</span><span class="sxs-lookup"><span data-stu-id="bffe1-108">[out] The array used to store the Signature tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="bffe1-109">no O tamanho máximo da `rSignatures` matriz.</span><span class="sxs-lookup"><span data-stu-id="bffe1-109">[in] The maximum size of the `rSignatures` array.</span></span>  
  
 `pcSignatures`  
 <span data-ttu-id="bffe1-110">fora O número de tokens de assinatura retornados em `rSignatures` .</span><span class="sxs-lookup"><span data-stu-id="bffe1-110">[out] The number of Signature tokens returned in `rSignatures`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bffe1-111">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="bffe1-111">Return Value</span></span>  
  
|<span data-ttu-id="bffe1-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bffe1-112">HRESULT</span></span>|<span data-ttu-id="bffe1-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="bffe1-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="bffe1-114">`EnumSignatures`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="bffe1-114">`EnumSignatures` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="bffe1-115">Não há tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="bffe1-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="bffe1-116">Nesse caso, `pcSignatures` é zero.</span><span class="sxs-lookup"><span data-stu-id="bffe1-116">In that case, `pcSignatures` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bffe1-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="bffe1-117">Remarks</span></span>  
 <span data-ttu-id="bffe1-118">Os tokens de assinatura são criados pelo método [IMetaDataEmit:: GetTokenFromSig](imetadataemit-gettokenfromsig-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bffe1-118">The Signature tokens are created by the [IMetaDataEmit::GetTokenFromSig](imetadataemit-gettokenfromsig-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bffe1-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bffe1-119">Requirements</span></span>  
 <span data-ttu-id="bffe1-120">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bffe1-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bffe1-121">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="bffe1-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bffe1-122">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bffe1-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bffe1-123">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bffe1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bffe1-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="bffe1-124">See also</span></span>

- [<span data-ttu-id="bffe1-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="bffe1-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="bffe1-126">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="bffe1-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
