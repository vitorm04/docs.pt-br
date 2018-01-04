---
title: "Método IMetaDataEmit::SaveToStream"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SaveToStream
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SaveToStream
helpviewer_keywords:
- IMetaDataEmit::SaveToStream method [.NET Framework metadata]
- SaveToStream method [.NET Framework metadata]
ms.assetid: e0290a49-3818-4a43-ad46-3014faa34f97
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 135faea41ab1a8165e315b8d0815abc48ba7fd38
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="4d910-102">Método IMetaDataEmit::SaveToStream</span><span class="sxs-lookup"><span data-stu-id="4d910-102">IMetaDataEmit::SaveToStream Method</span></span>
<span data-ttu-id="4d910-103">Salva todos os metadados no escopo atual especificado `IStream`.</span><span class="sxs-lookup"><span data-stu-id="4d910-103">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d910-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4d910-104">Syntax</span></span>  
  
```  
HRESULT SaveToStream (   
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4d910-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4d910-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="4d910-106">[in] O fluxo gravável para salvar.</span><span class="sxs-lookup"><span data-stu-id="4d910-106">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="4d910-107">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="4d910-107">[in] Reserved.</span></span> <span data-ttu-id="4d910-108">Deve ser zero.</span><span class="sxs-lookup"><span data-stu-id="4d910-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d910-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4d910-109">Requirements</span></span>  
 <span data-ttu-id="4d910-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d910-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d910-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4d910-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4d910-112">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="4d910-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4d910-113">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d910-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d910-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d910-114">See Also</span></span>  
 [<span data-ttu-id="4d910-115">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="4d910-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="4d910-116">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="4d910-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
