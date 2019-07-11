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
ms.openlocfilehash: 93ca394eb877a86e4242d5f9f18eb26f5628db7e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751080"
---
# <a name="imetadataemitsetfieldrva-method"></a><span data-ttu-id="3d6b8-102">Método IMetaDataEmit::SetFieldRVA</span><span class="sxs-lookup"><span data-stu-id="3d6b8-102">IMetaDataEmit::SetFieldRVA Method</span></span>
<span data-ttu-id="3d6b8-103">Define um valor da variável global para o endereço virtual relativo do campo referenciado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="3d6b8-103">Sets a global variable value for the relative virtual address of the field referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d6b8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3d6b8-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldRVA (   
    [in]  mdFieldDef  fd,   
    [in]  ULONG       ulRVA   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d6b8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3d6b8-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="3d6b8-106">[in] O token para o campo de destino.</span><span class="sxs-lookup"><span data-stu-id="3d6b8-106">[in] The token for the target field.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="3d6b8-107">[in] O endereço de uma área do código ou dados.</span><span class="sxs-lookup"><span data-stu-id="3d6b8-107">[in] The address of a code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d6b8-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3d6b8-108">Requirements</span></span>  
 <span data-ttu-id="3d6b8-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d6b8-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d6b8-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3d6b8-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3d6b8-111">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="3d6b8-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3d6b8-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d6b8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d6b8-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3d6b8-113">See also</span></span>

- [<span data-ttu-id="3d6b8-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="3d6b8-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="3d6b8-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="3d6b8-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
