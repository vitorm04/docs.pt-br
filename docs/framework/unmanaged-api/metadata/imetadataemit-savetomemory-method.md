---
title: Método IMetaDataEmit::SaveToMemory
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToMemory
helpviewer_keywords:
- IMetaDataEmit::SaveToMemory method [.NET Framework metadata]
- SaveToMemory method [.NET Framework metadata]
ms.assetid: d5237628-2675-45ed-a39e-65c0731b6a56
topic_type:
- apiref
ms.openlocfilehash: ccf82531eb1f78bcfc6762d10d53ffee59f30ad8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003928"
---
# <a name="imetadataemitsavetomemory-method"></a><span data-ttu-id="27f37-102">Método IMetaDataEmit::SaveToMemory</span><span class="sxs-lookup"><span data-stu-id="27f37-102">IMetaDataEmit::SaveToMemory Method</span></span>
<span data-ttu-id="27f37-103">Salva todos os metadados no escopo atual para a área especificada da memória.</span><span class="sxs-lookup"><span data-stu-id="27f37-103">Saves all metadata in the current scope to the specified area of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27f37-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="27f37-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveToMemory (
    [out]  void        *pbData,
    [in]   ULONG       cbData
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27f37-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="27f37-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="27f37-106">fora O endereço no qual começar a gravar metadados.</span><span class="sxs-lookup"><span data-stu-id="27f37-106">[out] The address at which to begin writing metadata.</span></span>  
  
 `cbData`  
 <span data-ttu-id="27f37-107">no O tamanho, em bytes, da memória alocada.</span><span class="sxs-lookup"><span data-stu-id="27f37-107">[in] The size, in bytes, of the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27f37-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="27f37-108">Requirements</span></span>  
 <span data-ttu-id="27f37-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27f37-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27f37-110">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="27f37-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="27f37-111">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="27f37-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="27f37-112">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27f37-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27f37-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="27f37-113">See also</span></span>

- [<span data-ttu-id="27f37-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="27f37-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="27f37-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="27f37-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
