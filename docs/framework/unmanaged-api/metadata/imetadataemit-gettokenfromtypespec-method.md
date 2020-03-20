---
title: Método IMetaDataEmit::GetTokenFromTypeSpec
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetTokenFromTypeSpec
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetTokenFromTypeSpec
helpviewer_keywords:
- GetTokenFromTypeSpec method [.NET Framework metadata]
- IMetaDataEmit::GetTokenFromTypeSpec method [.NET Framework metadata]
ms.assetid: 7de6447a-a751-49d8-87e2-951cee77b536
topic_type:
- apiref
ms.openlocfilehash: 8c609d730297881c0ac20dca8569f0e9492638e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175714"
---
# <a name="imetadataemitgettokenfromtypespec-method"></a><span data-ttu-id="646fe-102">Método IMetaDataEmit::GetTokenFromTypeSpec</span><span class="sxs-lookup"><span data-stu-id="646fe-102">IMetaDataEmit::GetTokenFromTypeSpec Method</span></span>
<span data-ttu-id="646fe-103">Obtém um token de metadados para o tipo com a assinatura de metadados especificada.</span><span class="sxs-lookup"><span data-stu-id="646fe-103">Gets a metadata token for the type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="646fe-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="646fe-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromTypeSpec (
    [in]  PCCOR_SIGNATURE       pvSig,
    [in]  ULONG                 cbSig,
    [out] mdTypeSpec            *ptypespec
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="646fe-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="646fe-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="646fe-106">[em] A assinatura está sendo definida.</span><span class="sxs-lookup"><span data-stu-id="646fe-106">[in] The signature being defined.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="646fe-107">[em] A contagem de `pvSig`bytes em .</span><span class="sxs-lookup"><span data-stu-id="646fe-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `ptypespec`  
 <span data-ttu-id="646fe-108">[fora] O `mdTypeSpec` token atribuído.</span><span class="sxs-lookup"><span data-stu-id="646fe-108">[out] The `mdTypeSpec` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="646fe-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="646fe-109">Requirements</span></span>  
 <span data-ttu-id="646fe-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="646fe-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="646fe-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="646fe-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="646fe-112">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="646fe-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="646fe-113">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="646fe-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="646fe-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="646fe-114">See also</span></span>

- [<span data-ttu-id="646fe-115">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="646fe-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="646fe-116">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="646fe-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
