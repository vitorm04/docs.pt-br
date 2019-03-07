---
title: Método IMetaDataEmit::SetFieldRVA
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldRVA
helpviewer_keywords:
- IMetaDataEmit::SetFieldRVA method [.NET Framework metadata]
- SetFieldRVA method [.NET Framework metadata]
ms.assetid: 6dc37f9d-87ee-4cb3-9216-ced600184ce8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9a38de994575bf0191ff2ab5ce1c7b047540289f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57470582"
---
# <a name="imetadataemitsetfieldrva-method"></a><span data-ttu-id="d53ae-102">Método IMetaDataEmit::SetFieldRVA</span><span class="sxs-lookup"><span data-stu-id="d53ae-102">IMetaDataEmit::SetFieldRVA Method</span></span>
<span data-ttu-id="d53ae-103">Define um valor da variável global para o endereço virtual relativo do campo referenciado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="d53ae-103">Sets a global variable value for the relative virtual address of the field referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d53ae-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d53ae-104">Syntax</span></span>  
  
```  
HRESULT SetFieldRVA (   
    [in]  mdFieldDef  fd,   
    [in]  ULONG       ulRVA   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d53ae-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d53ae-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="d53ae-106">[in] O token para o campo de destino.</span><span class="sxs-lookup"><span data-stu-id="d53ae-106">[in] The token for the target field.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="d53ae-107">[in] O endereço de uma área do código ou dados.</span><span class="sxs-lookup"><span data-stu-id="d53ae-107">[in] The address of a code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d53ae-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d53ae-108">Requirements</span></span>  
 <span data-ttu-id="d53ae-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d53ae-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d53ae-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d53ae-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d53ae-111">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="d53ae-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d53ae-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d53ae-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d53ae-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d53ae-113">See also</span></span>
- [<span data-ttu-id="d53ae-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="d53ae-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="d53ae-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="d53ae-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
