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
ms.openlocfilehash: f876187624d066b9e672fbf44a984d6d02a54c43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175870"
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="74fc7-102">Método IMetaDataEmit::ApplyEditAndContinue</span><span class="sxs-lookup"><span data-stu-id="74fc7-102">IMetaDataEmit::ApplyEditAndContinue Method</span></span>
<span data-ttu-id="74fc7-103">Atualiza o escopo de montagem atual com as alterações feitas nos metadados especificados.</span><span class="sxs-lookup"><span data-stu-id="74fc7-103">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74fc7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="74fc7-104">Syntax</span></span>  
  
```cpp  
HRESULT ApplyEditAndContinue (
    [in]  IUnknown    *pImport  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74fc7-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="74fc7-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="74fc7-106">\[em\] Pointer para um objeto [IUnknown](/cpp/atl/iunknown) que representa os metadados delta do arquivo executável portátil (PE).</span><span class="sxs-lookup"><span data-stu-id="74fc7-106">\[in\] Pointer to an [IUnknown](/cpp/atl/iunknown) object that represents the delta metadata from the portable executable (PE) file.</span></span>
  
 <span data-ttu-id="74fc7-107">Os metadados delta são o bloco de metadados que inclui as alterações que foram feitas na cópia dos metadados reais do módulo.</span><span class="sxs-lookup"><span data-stu-id="74fc7-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74fc7-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="74fc7-108">Requirements</span></span>  
 <span data-ttu-id="74fc7-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74fc7-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74fc7-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="74fc7-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="74fc7-111">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="74fc7-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="74fc7-112">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74fc7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74fc7-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="74fc7-113">See also</span></span>

- [<span data-ttu-id="74fc7-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="74fc7-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="74fc7-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="74fc7-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
