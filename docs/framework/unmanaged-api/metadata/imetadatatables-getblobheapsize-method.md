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
ms.openlocfilehash: c32407c3fc0bc5a045b80ec48937699826d981af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177161"
---
# <a name="imetadatatablesgetblobheapsize-method"></a><span data-ttu-id="07f93-102">Método IMetaDataTables::GetBlobHeapSize</span><span class="sxs-lookup"><span data-stu-id="07f93-102">IMetaDataTables::GetBlobHeapSize Method</span></span>
<span data-ttu-id="07f93-103">Obtém o tamanho, em bytes, do heap binário de objeto grande (BLOB).</span><span class="sxs-lookup"><span data-stu-id="07f93-103">Gets the size, in bytes, of the binary large object (BLOB) heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07f93-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="07f93-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlobHeapSize (  
    [out] ULONG     *pcbBlobs  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="07f93-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="07f93-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="07f93-106">[fora] Um ponteiro para o tamanho, em bytes, do monte BLOB.</span><span class="sxs-lookup"><span data-stu-id="07f93-106">[out] A pointer to the size, in bytes, of the BLOB heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07f93-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="07f93-107">Requirements</span></span>  
 <span data-ttu-id="07f93-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07f93-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07f93-109">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="07f93-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="07f93-110">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="07f93-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="07f93-111">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07f93-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07f93-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="07f93-112">See also</span></span>

- [<span data-ttu-id="07f93-113">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="07f93-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="07f93-114">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="07f93-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
