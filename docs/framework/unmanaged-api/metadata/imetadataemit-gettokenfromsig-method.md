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
ms.openlocfilehash: 740dad54bc3a79ff546176abdc35487d89ed8f44
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009243"
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="d12e6-102">Método IMetaDataEmit::GetTokenFromSig</span><span class="sxs-lookup"><span data-stu-id="d12e6-102">IMetaDataEmit::GetTokenFromSig Method</span></span>
<span data-ttu-id="d12e6-103">Obtém um token para a assinatura de metadados especificada.</span><span class="sxs-lookup"><span data-stu-id="d12e6-103">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d12e6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d12e6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromSig (
    [in]  PCCOR_SIGNATURE pvSig,
    [in]  ULONG       cbSig,
    [out] mdSignature *pmsig
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d12e6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d12e6-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="d12e6-106">no A assinatura a ser persistida e armazenada.</span><span class="sxs-lookup"><span data-stu-id="d12e6-106">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="d12e6-107">no A contagem de bytes em `pvSig` .</span><span class="sxs-lookup"><span data-stu-id="d12e6-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="d12e6-108">fora O `mdSignature` token atribuído.</span><span class="sxs-lookup"><span data-stu-id="d12e6-108">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d12e6-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d12e6-109">Requirements</span></span>  
 <span data-ttu-id="d12e6-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d12e6-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d12e6-111">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d12e6-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d12e6-112">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d12e6-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d12e6-113">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d12e6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d12e6-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="d12e6-114">See also</span></span>

- [<span data-ttu-id="d12e6-115">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="d12e6-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="d12e6-116">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="d12e6-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
