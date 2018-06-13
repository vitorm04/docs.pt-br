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
ms.openlocfilehash: be42fea034be4fe5d48874b00db86977a3039a34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448214"
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="12771-102">Método IMetaDataEmit::GetTokenFromSig</span><span class="sxs-lookup"><span data-stu-id="12771-102">IMetaDataEmit::GetTokenFromSig Method</span></span>
<span data-ttu-id="12771-103">Obtém um token para a assinatura de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="12771-103">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12771-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="12771-104">Syntax</span></span>  
  
```  
HRESULT GetTokenFromSig (   
    [in]  PCCOR_SIGNATURE pvSig,   
    [in]  ULONG       cbSig,   
    [out] mdSignature *pmsig   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="12771-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="12771-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="12771-106">[in] A assinatura seja mantida e armazenados.</span><span class="sxs-lookup"><span data-stu-id="12771-106">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="12771-107">[in] A contagem de bytes em `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="12771-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="12771-108">[out] O `mdSignature` token atribuído.</span><span class="sxs-lookup"><span data-stu-id="12771-108">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12771-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="12771-109">Requirements</span></span>  
 <span data-ttu-id="12771-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12771-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12771-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="12771-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="12771-112">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="12771-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="12771-113">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12771-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12771-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="12771-114">See Also</span></span>  
 [<span data-ttu-id="12771-115">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="12771-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="12771-116">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="12771-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
