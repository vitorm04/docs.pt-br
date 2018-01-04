---
title: "Método IMetaDataTables::GetStringHeapSize"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetStringHeapSize
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetStringHeapSize
helpviewer_keywords:
- IMetaDataTables::GetStringHeapSize method [.NET Framework metadata]
- GetStringHeapSize method [.NET Framework metadata]
ms.assetid: ed8f6335-81f5-4c09-81a9-2a909fc530c9
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f7ff6d6296e36d8d1a55682b453941b932bd590
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetstringheapsize-method"></a><span data-ttu-id="facfa-102">Método IMetaDataTables::GetStringHeapSize</span><span class="sxs-lookup"><span data-stu-id="facfa-102">IMetaDataTables::GetStringHeapSize Method</span></span>
<span data-ttu-id="facfa-103">Obtém o tamanho, em bytes, do heap de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="facfa-103">Gets the size, in bytes, of the string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="facfa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="facfa-104">Syntax</span></span>  
  
```  
HRESULT GetStringHeapSize (  
    [out] ULONG   *pcbStrings  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="facfa-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="facfa-105">Parameters</span></span>  
 `pcbStrings`  
 <span data-ttu-id="facfa-106">[out] Um ponteiro para o tamanho, em bytes, do heap de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="facfa-106">[out] A pointer to the size, in bytes, of the string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="facfa-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="facfa-107">Requirements</span></span>  
 <span data-ttu-id="facfa-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="facfa-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="facfa-109">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="facfa-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="facfa-110">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="facfa-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="facfa-111">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="facfa-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="facfa-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="facfa-112">See Also</span></span>  
 [<span data-ttu-id="facfa-113">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="facfa-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="facfa-114">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="facfa-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
