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
ms.openlocfilehash: f1262181fa745e1b6d3fc48a4ad728c1020705b5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434320"
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="e3837-102">Método IMetaDataEmit::GetTokenFromSig</span><span class="sxs-lookup"><span data-stu-id="e3837-102">IMetaDataEmit::GetTokenFromSig Method</span></span>
<span data-ttu-id="e3837-103">Obtém um token para a assinatura de metadados especificada.</span><span class="sxs-lookup"><span data-stu-id="e3837-103">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3837-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e3837-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromSig (   
    [in]  PCCOR_SIGNATURE pvSig,   
    [in]  ULONG       cbSig,   
    [out] mdSignature *pmsig   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3837-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e3837-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="e3837-106">no A assinatura a ser persistida e armazenada.</span><span class="sxs-lookup"><span data-stu-id="e3837-106">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="e3837-107">no A contagem de bytes em `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="e3837-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="e3837-108">fora O token de `mdSignature` atribuído.</span><span class="sxs-lookup"><span data-stu-id="e3837-108">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3837-109">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="e3837-109">Requirements</span></span>  
 <span data-ttu-id="e3837-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3837-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3837-111">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e3837-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e3837-112">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e3837-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e3837-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3837-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3837-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e3837-114">See also</span></span>

- [<span data-ttu-id="e3837-115">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="e3837-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="e3837-116">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="e3837-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
