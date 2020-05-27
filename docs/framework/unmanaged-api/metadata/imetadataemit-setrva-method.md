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
ms.openlocfilehash: 3059d30f3969b4e19cee5a8d7a34c606f3849c05
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008736"
---
# <a name="imetadataemitsetrva-method"></a><span data-ttu-id="b7b0d-102">Método IMetaDataEmit::SetRVA</span><span class="sxs-lookup"><span data-stu-id="b7b0d-102">IMetaDataEmit::SetRVA Method</span></span>
<span data-ttu-id="b7b0d-103">Define o endereço virtual relativo do método especificado.</span><span class="sxs-lookup"><span data-stu-id="b7b0d-103">Sets the relative virtual address of the specified method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7b0d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7b0d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetRVA (  
    [in]  mdMethodDef  md,
    [in]  ULONG        ulRVA
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7b0d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b7b0d-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="b7b0d-106">no O token para o método de destino ou a implementação do método.</span><span class="sxs-lookup"><span data-stu-id="b7b0d-106">[in] The token for the target method or method implementation.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="b7b0d-107">no O endereço do código ou da área de dados.</span><span class="sxs-lookup"><span data-stu-id="b7b0d-107">[in] The address of the code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7b0d-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b7b0d-108">Requirements</span></span>  
 <span data-ttu-id="b7b0d-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7b0d-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7b0d-110">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b7b0d-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b7b0d-111">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b7b0d-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b7b0d-112">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7b0d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7b0d-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="b7b0d-113">See also</span></span>

- [<span data-ttu-id="b7b0d-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="b7b0d-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="b7b0d-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="b7b0d-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
