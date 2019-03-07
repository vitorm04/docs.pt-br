---
title: Método IMetaDataTables::GetUserStringHeapSize
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetUserStringHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserStringHeapSize
helpviewer_keywords:
- IMetaDataTables::GetUserStringHeapSize method [.NET Framework metadata]
- GetUserStringHeapSize method [.NET Framework metadata]
ms.assetid: cba9e4d6-9461-4420-9614-96ff7039ec9c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1215da0816c1fc7cdfaee0da167118909f8e5eb3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466096"
---
# <a name="imetadatatablesgetuserstringheapsize-method"></a><span data-ttu-id="da7b1-102">Método IMetaDataTables::GetUserStringHeapSize</span><span class="sxs-lookup"><span data-stu-id="da7b1-102">IMetaDataTables::GetUserStringHeapSize Method</span></span>
<span data-ttu-id="da7b1-103">Obtém o tamanho, em bytes, do heap de cadeia de caracteres de usuário.</span><span class="sxs-lookup"><span data-stu-id="da7b1-103">Gets the size, in bytes, of the user string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da7b1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="da7b1-104">Syntax</span></span>  
  
```  
HRESULT GetUserStringHeapSize (  
    [out] ULONG   *pcbBlobs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da7b1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="da7b1-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="da7b1-106">[out] Um ponteiro para o tamanho, em bytes, do heap de cadeia de caracteres de usuário.</span><span class="sxs-lookup"><span data-stu-id="da7b1-106">[out] A pointer to the size, in bytes, of the user string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da7b1-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="da7b1-107">Requirements</span></span>  
 <span data-ttu-id="da7b1-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da7b1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da7b1-109">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="da7b1-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="da7b1-110">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="da7b1-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="da7b1-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da7b1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da7b1-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="da7b1-112">See also</span></span>
- [<span data-ttu-id="da7b1-113">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="da7b1-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="da7b1-114">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="da7b1-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
