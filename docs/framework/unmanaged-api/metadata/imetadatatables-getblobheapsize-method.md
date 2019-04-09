---
title: Método IMetaDataTables::GetBlobHeapSize
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetBlobHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetBlobHeapSize
helpviewer_keywords:
- GetBlobHeapSize method [.NET Framework metadata]
- IMetaDataTables::GetBlobHeapSize method [.NET Framework metadata]
ms.assetid: 6330a9ee-8cd5-4299-86f1-b4de2c701a0d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d22e61d28e0fbf06fa1cfe9e9ac18a534726f01d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076449"
---
# <a name="imetadatatablesgetblobheapsize-method"></a><span data-ttu-id="791d7-102">Método IMetaDataTables::GetBlobHeapSize</span><span class="sxs-lookup"><span data-stu-id="791d7-102">IMetaDataTables::GetBlobHeapSize Method</span></span>
<span data-ttu-id="791d7-103">Obtém o tamanho, em bytes, do heap de objeto binário grande (BLOB).</span><span class="sxs-lookup"><span data-stu-id="791d7-103">Gets the size, in bytes, of the binary large object (BLOB) heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="791d7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="791d7-104">Syntax</span></span>  
  
```  
HRESULT GetBlobHeapSize (  
    [out] ULONG     *pcbBlobs  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="791d7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="791d7-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="791d7-106">[out] Um ponteiro para o tamanho, em bytes, do heap de BLOB.</span><span class="sxs-lookup"><span data-stu-id="791d7-106">[out] A pointer to the size, in bytes, of the BLOB heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="791d7-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="791d7-107">Requirements</span></span>  
 <span data-ttu-id="791d7-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="791d7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="791d7-109">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="791d7-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="791d7-110">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="791d7-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="791d7-111">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="791d7-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="791d7-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="791d7-112">See also</span></span>

- [<span data-ttu-id="791d7-113">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="791d7-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="791d7-114">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="791d7-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
