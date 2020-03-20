---
title: Método IMetaDataEmit::SetRVA
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetRVA
helpviewer_keywords:
- IMetaDataEmit::SetRVA method [.NET Framework metadata]
- SetRVA method [.NET Framework metadata]
ms.assetid: 4d69fb6d-ee35-4318-8224-5eea2bd16818
topic_type:
- apiref
ms.openlocfilehash: fe0b4b7fef0d05c4acc06dad5bc8a4eaf0722c9c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175571"
---
# <a name="imetadataemitsetrva-method"></a><span data-ttu-id="4423b-102">Método IMetaDataEmit::SetRVA</span><span class="sxs-lookup"><span data-stu-id="4423b-102">IMetaDataEmit::SetRVA Method</span></span>
<span data-ttu-id="4423b-103">Define o endereço virtual relativo do método especificado.</span><span class="sxs-lookup"><span data-stu-id="4423b-103">Sets the relative virtual address of the specified method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4423b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4423b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetRVA (  
    [in]  mdMethodDef  md,
    [in]  ULONG        ulRVA
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4423b-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="4423b-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="4423b-106">[em] O token para a implementação do método de destino ou método.</span><span class="sxs-lookup"><span data-stu-id="4423b-106">[in] The token for the target method or method implementation.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="4423b-107">[em] O endereço do código ou área de dados.</span><span class="sxs-lookup"><span data-stu-id="4423b-107">[in] The address of the code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4423b-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4423b-108">Requirements</span></span>  
 <span data-ttu-id="4423b-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4423b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4423b-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4423b-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4423b-111">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4423b-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4423b-112">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4423b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4423b-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="4423b-113">See also</span></span>

- [<span data-ttu-id="4423b-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="4423b-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="4423b-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="4423b-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
