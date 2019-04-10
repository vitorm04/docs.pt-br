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
ms.openlocfilehash: c18c72ecbaf2e0d3153ad7f00caf73421e35fa0a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225307"
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="50ecd-102">Método IMetaDataEmit::ApplyEditAndContinue</span><span class="sxs-lookup"><span data-stu-id="50ecd-102">IMetaDataEmit::ApplyEditAndContinue Method</span></span>
<span data-ttu-id="50ecd-103">Atualiza o escopo do assembly atual com as alterações feitas nos metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="50ecd-103">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50ecd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="50ecd-104">Syntax</span></span>  
  
```  
HRESULT ApplyEditAndContinue (   
    [in]  IUnknown    *pImport  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50ecd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="50ecd-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="50ecd-106">\[na\] ponteiro para um [IUnknown](/cpp/atl/iunknown) objeto que representa os metadados de delta do arquivo executável portátil (PE).</span><span class="sxs-lookup"><span data-stu-id="50ecd-106">\[in\] Pointer to an [IUnknown](/cpp/atl/iunknown) object that represents the delta metadata from the portable executable (PE) file.</span></span>
  
 <span data-ttu-id="50ecd-107">Os metadados de delta são o bloco de metadados que inclui as alterações que foram feitas para a cópia dos metadados do módulo.</span><span class="sxs-lookup"><span data-stu-id="50ecd-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50ecd-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="50ecd-108">Requirements</span></span>  
 <span data-ttu-id="50ecd-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50ecd-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50ecd-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="50ecd-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="50ecd-111">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="50ecd-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="50ecd-112">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="50ecd-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="50ecd-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="50ecd-113">See also</span></span>

- [<span data-ttu-id="50ecd-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="50ecd-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="50ecd-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="50ecd-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
