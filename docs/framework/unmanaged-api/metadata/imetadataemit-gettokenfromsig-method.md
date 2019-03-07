---
title: Método IMetaDataEmit::GetTokenFromSig
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetTokenFromSig
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetTokenFromSig
helpviewer_keywords:
- IMetaDataEmit::GetTokenFromSig method [.NET Framework metadata]
- GetTokenFromSig method [.NET Framework metadata]
ms.assetid: 50a58a83-6287-40a4-b315-47823cea0a5c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2f94c12654626e149b0f75327e8fdfa55aefe697
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57467106"
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="a3d85-102">Método IMetaDataEmit::GetTokenFromSig</span><span class="sxs-lookup"><span data-stu-id="a3d85-102">IMetaDataEmit::GetTokenFromSig Method</span></span>
<span data-ttu-id="a3d85-103">Obtém um token para a assinatura de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="a3d85-103">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3d85-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a3d85-104">Syntax</span></span>  
  
```  
HRESULT GetTokenFromSig (   
    [in]  PCCOR_SIGNATURE pvSig,   
    [in]  ULONG       cbSig,   
    [out] mdSignature *pmsig   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3d85-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a3d85-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="a3d85-106">[in] A assinatura ser persistidos e armazenados.</span><span class="sxs-lookup"><span data-stu-id="a3d85-106">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="a3d85-107">[in] A contagem de bytes em `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="a3d85-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="a3d85-108">[out] O `mdSignature` token atribuído.</span><span class="sxs-lookup"><span data-stu-id="a3d85-108">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3d85-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a3d85-109">Requirements</span></span>  
 <span data-ttu-id="a3d85-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3d85-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3d85-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a3d85-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a3d85-112">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="a3d85-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a3d85-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3d85-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3d85-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a3d85-114">See also</span></span>
- [<span data-ttu-id="a3d85-115">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="a3d85-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="a3d85-116">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="a3d85-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
