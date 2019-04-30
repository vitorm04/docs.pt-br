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
ms.openlocfilehash: 4ebde1d506a120a99e1c637c660b45d698994f5a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992466"
---
# <a name="imetadataemitsetfieldrva-method"></a><span data-ttu-id="6c3c4-102">Método IMetaDataEmit::SetFieldRVA</span><span class="sxs-lookup"><span data-stu-id="6c3c4-102">IMetaDataEmit::SetFieldRVA Method</span></span>
<span data-ttu-id="6c3c4-103">Define um valor da variável global para o endereço virtual relativo do campo referenciado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="6c3c4-103">Sets a global variable value for the relative virtual address of the field referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c3c4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6c3c4-104">Syntax</span></span>  
  
```  
HRESULT SetFieldRVA (   
    [in]  mdFieldDef  fd,   
    [in]  ULONG       ulRVA   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c3c4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6c3c4-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="6c3c4-106">[in] O token para o campo de destino.</span><span class="sxs-lookup"><span data-stu-id="6c3c4-106">[in] The token for the target field.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="6c3c4-107">[in] O endereço de uma área do código ou dados.</span><span class="sxs-lookup"><span data-stu-id="6c3c4-107">[in] The address of a code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c3c4-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6c3c4-108">Requirements</span></span>  
 <span data-ttu-id="6c3c4-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c3c4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c3c4-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6c3c4-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6c3c4-111">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="6c3c4-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6c3c4-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c3c4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c3c4-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6c3c4-113">See also</span></span>

- [<span data-ttu-id="6c3c4-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="6c3c4-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="6c3c4-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="6c3c4-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
