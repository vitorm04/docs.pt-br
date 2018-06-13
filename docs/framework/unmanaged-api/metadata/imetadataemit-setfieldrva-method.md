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
ms.openlocfilehash: 0447a44c555e141c96d6a52ba330e181151a7bc7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445884"
---
# <a name="imetadataemitsetfieldrva-method"></a><span data-ttu-id="fb710-102">Método IMetaDataEmit::SetFieldRVA</span><span class="sxs-lookup"><span data-stu-id="fb710-102">IMetaDataEmit::SetFieldRVA Method</span></span>
<span data-ttu-id="fb710-103">Define um valor de variável global para o endereço virtual relativo do campo referenciado por token especificado.</span><span class="sxs-lookup"><span data-stu-id="fb710-103">Sets a global variable value for the relative virtual address of the field referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb710-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fb710-104">Syntax</span></span>  
  
```  
HRESULT SetFieldRVA (   
    [in]  mdFieldDef  fd,   
    [in]  ULONG       ulRVA   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb710-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fb710-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="fb710-106">[in] O token para o campo de destino.</span><span class="sxs-lookup"><span data-stu-id="fb710-106">[in] The token for the target field.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="fb710-107">[in] O endereço de uma área de códigos ou dados.</span><span class="sxs-lookup"><span data-stu-id="fb710-107">[in] The address of a code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb710-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fb710-108">Requirements</span></span>  
 <span data-ttu-id="fb710-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb710-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb710-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fb710-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fb710-111">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="fb710-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fb710-112">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb710-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb710-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fb710-113">See Also</span></span>  
 [<span data-ttu-id="fb710-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="fb710-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="fb710-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="fb710-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
