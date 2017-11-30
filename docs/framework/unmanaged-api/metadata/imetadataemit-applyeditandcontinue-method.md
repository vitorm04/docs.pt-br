---
title: "Método IMetaDataEmit::ApplyEditAndContinue"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.ApplyEditAndContinue
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::ApplyEditAndContinue
helpviewer_keywords:
- ApplyEditAndContinue method [.NET Framework metadata]
- IMetaDataEmit::ApplyEditAndContinue method [.NET Framework metadata]
ms.assetid: 35991289-f389-495d-8caa-a6384fb1d557
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6d7744051bca9aeec677803f8b6c0bbbd0cdd1fd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="1f5fb-102">Método IMetaDataEmit::ApplyEditAndContinue</span><span class="sxs-lookup"><span data-stu-id="1f5fb-102">IMetaDataEmit::ApplyEditAndContinue Method</span></span>
<span data-ttu-id="1f5fb-103">Atualiza o escopo do assembly atual com as alterações feitas nos metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="1f5fb-103">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f5fb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1f5fb-104">Syntax</span></span>  
  
```  
HRESULT ApplyEditAndContinue (   
    [in]  IUnknown    *pImport  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1f5fb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1f5fb-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="1f5fb-106">[in] Ponteiro para um <<!--zzxref:IUnknown --> `IUnknown`> objeto que representa os metadados de delta do arquivo PE (executável portátil).</span><span class="sxs-lookup"><span data-stu-id="1f5fb-106">[in] Pointer to an <<!--zzxref:IUnknown --> `IUnknown`> object that represents the delta metadata from the portable executable (PE) file.</span></span>  
  
 <span data-ttu-id="1f5fb-107">Os metadados de delta são o bloco de metadados que incluem as alterações que foram feitas para a cópia de metadados real do módulo.</span><span class="sxs-lookup"><span data-stu-id="1f5fb-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f5fb-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1f5fb-108">Requirements</span></span>  
 <span data-ttu-id="1f5fb-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f5fb-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f5fb-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1f5fb-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1f5fb-111">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="1f5fb-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1f5fb-112">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f5fb-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f5fb-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1f5fb-113">See Also</span></span>  
 [<span data-ttu-id="1f5fb-114">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="1f5fb-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="1f5fb-115">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="1f5fb-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
