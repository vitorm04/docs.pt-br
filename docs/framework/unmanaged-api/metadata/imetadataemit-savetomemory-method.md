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
ms.openlocfilehash: b680e807554a60711e61729680e9c9fcf1c8fdaa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446173"
---
# <a name="imetadataemitsavetomemory-method"></a><span data-ttu-id="f0dd1-102">Método IMetaDataEmit::SaveToMemory</span><span class="sxs-lookup"><span data-stu-id="f0dd1-102">IMetaDataEmit::SaveToMemory Method</span></span>
<span data-ttu-id="f0dd1-103">Salva todos os metadados no escopo atual para a área especificada de memória.</span><span class="sxs-lookup"><span data-stu-id="f0dd1-103">Saves all metadata in the current scope to the specified area of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0dd1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f0dd1-104">Syntax</span></span>  
  
```  
HRESULT SaveToMemory (   
    [out]  void        *pbData,   
    [in]   ULONG       cbData   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f0dd1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f0dd1-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="f0dd1-106">[out] O endereço no qual começar a gravar metadados.</span><span class="sxs-lookup"><span data-stu-id="f0dd1-106">[out] The address at which to begin writing metadata.</span></span>  
  
 `cbData`  
 <span data-ttu-id="f0dd1-107">[in] O tamanho, em bytes, da memória alocada.</span><span class="sxs-lookup"><span data-stu-id="f0dd1-107">[in] The size, in bytes, of the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0dd1-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f0dd1-108">Requirements</span></span>  
 <span data-ttu-id="f0dd1-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0dd1-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0dd1-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f0dd1-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f0dd1-111">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="f0dd1-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f0dd1-112">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0dd1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0dd1-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f0dd1-113">See Also</span></span>  
 [<span data-ttu-id="f0dd1-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="f0dd1-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="f0dd1-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="f0dd1-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
