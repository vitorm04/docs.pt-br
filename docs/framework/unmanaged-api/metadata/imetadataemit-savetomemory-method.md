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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bc840df9dd0793a7347b7f0d8a05296a09d634c8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59192102"
---
# <a name="imetadataemitsavetomemory-method"></a><span data-ttu-id="f3129-102">Método IMetaDataEmit::SaveToMemory</span><span class="sxs-lookup"><span data-stu-id="f3129-102">IMetaDataEmit::SaveToMemory Method</span></span>
<span data-ttu-id="f3129-103">Salva todos os metadados no escopo atual para a área especificada de memória.</span><span class="sxs-lookup"><span data-stu-id="f3129-103">Saves all metadata in the current scope to the specified area of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3129-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f3129-104">Syntax</span></span>  
  
```  
HRESULT SaveToMemory (   
    [out]  void        *pbData,   
    [in]   ULONG       cbData   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3129-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f3129-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="f3129-106">[out] O endereço no qual será iniciada a gravação de metadados.</span><span class="sxs-lookup"><span data-stu-id="f3129-106">[out] The address at which to begin writing metadata.</span></span>  
  
 `cbData`  
 <span data-ttu-id="f3129-107">[in] O tamanho, em bytes, da memória alocada.</span><span class="sxs-lookup"><span data-stu-id="f3129-107">[in] The size, in bytes, of the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3129-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f3129-108">Requirements</span></span>  
 <span data-ttu-id="f3129-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3129-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3129-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f3129-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f3129-111">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f3129-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="f3129-112">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="f3129-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f3129-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3129-113">See also</span></span>

- [<span data-ttu-id="f3129-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="f3129-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f3129-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="f3129-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
