---
title: Método IMetaDataTables::GetGuidHeapSize
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuidHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuidHeapSize
helpviewer_keywords:
- GetGuidHeapSize method [.NET Framework metadata]
- IMetaDataTables::GetGuidHeapSize method [.NET Framework metadata]
ms.assetid: e875cbee-1ad9-4f1a-bf03-38cdb8ff371a
topic_type:
- apiref
ms.openlocfilehash: 71a75defa72e4fe3594b4d0ceff45273b3a35395
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490348"
---
# <a name="imetadatatablesgetguidheapsize-method"></a><span data-ttu-id="67f6d-102">Método IMetaDataTables::GetGuidHeapSize</span><span class="sxs-lookup"><span data-stu-id="67f6d-102">IMetaDataTables::GetGuidHeapSize Method</span></span>
<span data-ttu-id="67f6d-103">Obtém o tamanho, em bytes, do heap GUID.</span><span class="sxs-lookup"><span data-stu-id="67f6d-103">Gets the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67f6d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="67f6d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGuidHeapSize (  
    [out] ULONG   *pcbGuids  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67f6d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="67f6d-105">Parameters</span></span>  
 `pcbGuids`  
 <span data-ttu-id="67f6d-106">fora Um ponteiro para o tamanho, em bytes, do heap GUID.</span><span class="sxs-lookup"><span data-stu-id="67f6d-106">[out] A pointer to the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67f6d-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="67f6d-107">Requirements</span></span>  
 <span data-ttu-id="67f6d-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67f6d-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67f6d-109">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="67f6d-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="67f6d-110">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="67f6d-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="67f6d-111">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67f6d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67f6d-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="67f6d-112">See also</span></span>

- [<span data-ttu-id="67f6d-113">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="67f6d-113">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="67f6d-114">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="67f6d-114">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
