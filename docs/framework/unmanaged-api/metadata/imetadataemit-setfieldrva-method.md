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
ms.openlocfilehash: 7648a1b3d219ee5d2b1ddc6b26f7b65c9ac85105
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175636"
---
# <a name="imetadataemitsetfieldrva-method"></a><span data-ttu-id="402f7-102">Método IMetaDataEmit::SetFieldRVA</span><span class="sxs-lookup"><span data-stu-id="402f7-102">IMetaDataEmit::SetFieldRVA Method</span></span>
<span data-ttu-id="402f7-103">Define um valor variável global para o endereço virtual relativo do campo referenciado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="402f7-103">Sets a global variable value for the relative virtual address of the field referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="402f7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="402f7-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldRVA (
    [in]  mdFieldDef  fd,
    [in]  ULONG       ulRVA
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="402f7-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="402f7-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="402f7-106">[em] O símbolo para o campo alvo.</span><span class="sxs-lookup"><span data-stu-id="402f7-106">[in] The token for the target field.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="402f7-107">[em] O endereço de um código ou área de dados.</span><span class="sxs-lookup"><span data-stu-id="402f7-107">[in] The address of a code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="402f7-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="402f7-108">Requirements</span></span>  
 <span data-ttu-id="402f7-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="402f7-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="402f7-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="402f7-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="402f7-111">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="402f7-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="402f7-112">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="402f7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="402f7-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="402f7-113">See also</span></span>

- [<span data-ttu-id="402f7-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="402f7-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="402f7-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="402f7-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
