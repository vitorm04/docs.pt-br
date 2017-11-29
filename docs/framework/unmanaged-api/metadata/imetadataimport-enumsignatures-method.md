---
title: "Método IMetaDataImport::EnumSignatures"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumSignatures
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumSignatures
helpviewer_keywords:
- EnumSignatures method [.NET Framework metadata]
- IMetaDataImport::EnumSignatures method [.NET Framework metadata]
ms.assetid: d0d65060-6f90-42a2-95cf-6ffb04352996
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 25fb32b0780dc91157d39ece37f93d7abd582cf7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumsignatures-method"></a><span data-ttu-id="a021d-102">Método IMetaDataImport::EnumSignatures</span><span class="sxs-lookup"><span data-stu-id="a021d-102">IMetaDataImport::EnumSignatures Method</span></span>
<span data-ttu-id="a021d-103">Enumera os tokens de assinatura que representa as assinaturas autônomas no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="a021d-103">Enumerates Signature tokens representing stand-alone signatures in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a021d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a021d-104">Syntax</span></span>  
  
```  
HRESULT EnumSignatures (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdSignature  rSignatures[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcSignatures  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a021d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a021d-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="a021d-106">[out no] Um ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="a021d-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="a021d-107">Isso deve ser NULL para a primeira chamada do método.</span><span class="sxs-lookup"><span data-stu-id="a021d-107">This must be NULL for the first call of this method.</span></span>  
  
 `rSignatures`  
 <span data-ttu-id="a021d-108">[out] A matriz usada para armazenar os tokens de assinatura.</span><span class="sxs-lookup"><span data-stu-id="a021d-108">[out] The array used to store the Signature tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a021d-109">[in] O tamanho máximo da `rSignatures` matriz.</span><span class="sxs-lookup"><span data-stu-id="a021d-109">[in] The maximum size of the `rSignatures` array.</span></span>  
  
 `pcSignatures`  
 <span data-ttu-id="a021d-110">[out] O número de tokens de assinatura retornada em `rSignatures`.</span><span class="sxs-lookup"><span data-stu-id="a021d-110">[out] The number of Signature tokens returned in `rSignatures`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a021d-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a021d-111">Return Value</span></span>  
  
|<span data-ttu-id="a021d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a021d-112">HRESULT</span></span>|<span data-ttu-id="a021d-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="a021d-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a021d-114">`EnumSignatures`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="a021d-114">`EnumSignatures` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a021d-115">Não há nenhum tokens para enumerar.</span><span class="sxs-lookup"><span data-stu-id="a021d-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="a021d-116">Nesse caso, `pcSignatures` é zero.</span><span class="sxs-lookup"><span data-stu-id="a021d-116">In that case, `pcSignatures` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a021d-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="a021d-117">Remarks</span></span>  
 <span data-ttu-id="a021d-118">Os tokens de assinatura são criados pelo [: Gettokenfromsig](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="a021d-118">The Signature tokens are created by the [IMetaDataEmit::GetTokenFromSig](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a021d-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a021d-119">Requirements</span></span>  
 <span data-ttu-id="a021d-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a021d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a021d-121">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a021d-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a021d-122">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="a021d-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a021d-123">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a021d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a021d-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a021d-124">See Also</span></span>  
 [<span data-ttu-id="a021d-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="a021d-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="a021d-126">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="a021d-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
