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
ms.openlocfilehash: d02943f28435fc00aad8e319aa260a24cca5e307
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177596"
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="14f7c-102">Método IMetaDataEmit::GetTokenFromSig</span><span class="sxs-lookup"><span data-stu-id="14f7c-102">IMetaDataEmit::GetTokenFromSig Method</span></span>
<span data-ttu-id="14f7c-103">Obtém um token para a assinatura de metadados especificada.</span><span class="sxs-lookup"><span data-stu-id="14f7c-103">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14f7c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="14f7c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromSig (
    [in]  PCCOR_SIGNATURE pvSig,
    [in]  ULONG       cbSig,
    [out] mdSignature *pmsig
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14f7c-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="14f7c-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="14f7c-106">[em] A assinatura a ser persistida e armazenada.</span><span class="sxs-lookup"><span data-stu-id="14f7c-106">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="14f7c-107">[em] A contagem de `pvSig`bytes em .</span><span class="sxs-lookup"><span data-stu-id="14f7c-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="14f7c-108">[fora] O `mdSignature` token atribuído.</span><span class="sxs-lookup"><span data-stu-id="14f7c-108">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14f7c-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="14f7c-109">Requirements</span></span>  
 <span data-ttu-id="14f7c-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14f7c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14f7c-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="14f7c-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="14f7c-112">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="14f7c-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="14f7c-113">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14f7c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14f7c-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="14f7c-114">See also</span></span>

- [<span data-ttu-id="14f7c-115">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="14f7c-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="14f7c-116">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="14f7c-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
