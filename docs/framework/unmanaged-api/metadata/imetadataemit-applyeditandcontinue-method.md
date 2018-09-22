---
title: Método IMetaDataEmit::ApplyEditAndContinue
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.ApplyEditAndContinue
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::ApplyEditAndContinue
helpviewer_keywords:
- ApplyEditAndContinue method [.NET Framework metadata]
- IMetaDataEmit::ApplyEditAndContinue method [.NET Framework metadata]
ms.assetid: 35991289-f389-495d-8caa-a6384fb1d557
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: faa9bc412e67e0e49ee969bd8b246a424fe628a0
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46583896"
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="9630d-102">Método IMetaDataEmit::ApplyEditAndContinue</span><span class="sxs-lookup"><span data-stu-id="9630d-102">IMetaDataEmit::ApplyEditAndContinue Method</span></span>
<span data-ttu-id="9630d-103">Atualiza o escopo do assembly atual com as alterações feitas nos metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="9630d-103">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9630d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9630d-104">Syntax</span></span>  
  
```  
HRESULT ApplyEditAndContinue (   
    [in]  IUnknown    *pImport  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9630d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9630d-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="9630d-106">\[na\] ponteiro para um [IUnknown](/cpp/atl/iunknown) objeto que representa os metadados de delta do arquivo executável portátil (PE).</span><span class="sxs-lookup"><span data-stu-id="9630d-106">\[in\] Pointer to an [IUnknown](/cpp/atl/iunknown) object that represents the delta metadata from the portable executable (PE) file.</span></span>
  
 <span data-ttu-id="9630d-107">Os metadados de delta são o bloco de metadados que inclui as alterações que foram feitas para a cópia dos metadados do módulo.</span><span class="sxs-lookup"><span data-stu-id="9630d-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9630d-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9630d-108">Requirements</span></span>  
 <span data-ttu-id="9630d-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9630d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9630d-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9630d-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9630d-111">**Biblioteca:** usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="9630d-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9630d-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9630d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9630d-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9630d-113">See Also</span></span>  
 [<span data-ttu-id="9630d-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="9630d-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="9630d-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="9630d-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
