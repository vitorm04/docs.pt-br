---
title: Método IMetaDataTables::GetStringHeapSize
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetStringHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetStringHeapSize
helpviewer_keywords:
- IMetaDataTables::GetStringHeapSize method [.NET Framework metadata]
- GetStringHeapSize method [.NET Framework metadata]
ms.assetid: ed8f6335-81f5-4c09-81a9-2a909fc530c9
topic_type:
- apiref
ms.openlocfilehash: 43599a7e39ca4cc9d27dab43a948dc2f04e5010a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426675"
---
# <a name="imetadatatablesgetstringheapsize-method"></a><span data-ttu-id="72e3c-102">Método IMetaDataTables::GetStringHeapSize</span><span class="sxs-lookup"><span data-stu-id="72e3c-102">IMetaDataTables::GetStringHeapSize Method</span></span>
<span data-ttu-id="72e3c-103">Obtém o tamanho, em bytes, do heap de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="72e3c-103">Gets the size, in bytes, of the string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72e3c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="72e3c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStringHeapSize (  
    [out] ULONG   *pcbStrings  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72e3c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72e3c-105">Parameters</span></span>  
 `pcbStrings`  
 <span data-ttu-id="72e3c-106">fora Um ponteiro para o tamanho, em bytes, do heap de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="72e3c-106">[out] A pointer to the size, in bytes, of the string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72e3c-107">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="72e3c-107">Requirements</span></span>  
 <span data-ttu-id="72e3c-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72e3c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72e3c-109">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="72e3c-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="72e3c-110">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="72e3c-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="72e3c-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72e3c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72e3c-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72e3c-112">See also</span></span>

- [<span data-ttu-id="72e3c-113">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="72e3c-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="72e3c-114">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="72e3c-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
