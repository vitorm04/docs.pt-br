---
title: "Método IMetaDataEmit::ApplyEditAndContinue"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b4d6f378c4da884cffc6827f700586cee745642b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="8fc78-102">Método IMetaDataEmit::ApplyEditAndContinue</span><span class="sxs-lookup"><span data-stu-id="8fc78-102">IMetaDataEmit::ApplyEditAndContinue Method</span></span>
<span data-ttu-id="8fc78-103">Atualiza o escopo do assembly atual com as alterações feitas nos metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="8fc78-103">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fc78-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8fc78-104">Syntax</span></span>  
  
```  
HRESULT ApplyEditAndContinue (   
    [in]  IUnknown    *pImport  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8fc78-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8fc78-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="8fc78-106">[in] Ponteiro para um <<!--zzxref:IUnknown --> `IUnknown`> objeto que representa os metadados de delta do arquivo PE (executável portátil).</span><span class="sxs-lookup"><span data-stu-id="8fc78-106">[in] Pointer to an <<!--zzxref:IUnknown --> `IUnknown`> object that represents the delta metadata from the portable executable (PE) file.</span></span>  
  
 <span data-ttu-id="8fc78-107">Os metadados de delta são o bloco de metadados que incluem as alterações que foram feitas para a cópia de metadados real do módulo.</span><span class="sxs-lookup"><span data-stu-id="8fc78-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fc78-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8fc78-108">Requirements</span></span>  
 <span data-ttu-id="8fc78-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fc78-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fc78-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8fc78-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8fc78-111">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="8fc78-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8fc78-112">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fc78-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fc78-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8fc78-113">See Also</span></span>  
 [<span data-ttu-id="8fc78-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="8fc78-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="8fc78-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="8fc78-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
