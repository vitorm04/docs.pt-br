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
ms.openlocfilehash: d0558154dc64ca95a691f36fb67586d570caa888
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484986"
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="5c1e1-102">Método IMetaDataEmit::ApplyEditAndContinue</span><span class="sxs-lookup"><span data-stu-id="5c1e1-102">IMetaDataEmit::ApplyEditAndContinue Method</span></span>
<span data-ttu-id="5c1e1-103">Atualiza o escopo do assembly atual com as alterações feitas nos metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="5c1e1-103">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c1e1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5c1e1-104">Syntax</span></span>  
  
```  
HRESULT ApplyEditAndContinue (   
    [in]  IUnknown    *pImport  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c1e1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5c1e1-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="5c1e1-106">\[na\] ponteiro para um [IUnknown](/cpp/atl/iunknown) objeto que representa os metadados de delta do arquivo executável portátil (PE).</span><span class="sxs-lookup"><span data-stu-id="5c1e1-106">\[in\] Pointer to an [IUnknown](/cpp/atl/iunknown) object that represents the delta metadata from the portable executable (PE) file.</span></span>
  
 <span data-ttu-id="5c1e1-107">Os metadados de delta são o bloco de metadados que inclui as alterações que foram feitas para a cópia dos metadados do módulo.</span><span class="sxs-lookup"><span data-stu-id="5c1e1-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c1e1-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5c1e1-108">Requirements</span></span>  
 <span data-ttu-id="5c1e1-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c1e1-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c1e1-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5c1e1-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5c1e1-111">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="5c1e1-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c1e1-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c1e1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c1e1-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5c1e1-113">See also</span></span>
- [<span data-ttu-id="5c1e1-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="5c1e1-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="5c1e1-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="5c1e1-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
