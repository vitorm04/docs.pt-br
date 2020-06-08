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
ms.openlocfilehash: 1aa7853602c1aaf484ef89d9c4fb06464e135f80
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501151"
---
# <a name="imetadatatablesgetstringheapsize-method"></a><span data-ttu-id="90666-102">Método IMetaDataTables::GetStringHeapSize</span><span class="sxs-lookup"><span data-stu-id="90666-102">IMetaDataTables::GetStringHeapSize Method</span></span>
<span data-ttu-id="90666-103">Obtém o tamanho, em bytes, do heap de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="90666-103">Gets the size, in bytes, of the string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90666-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="90666-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStringHeapSize (  
    [out] ULONG   *pcbStrings  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90666-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="90666-105">Parameters</span></span>  
 `pcbStrings`  
 <span data-ttu-id="90666-106">fora Um ponteiro para o tamanho, em bytes, do heap de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="90666-106">[out] A pointer to the size, in bytes, of the string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90666-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="90666-107">Requirements</span></span>  
 <span data-ttu-id="90666-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90666-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90666-109">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="90666-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="90666-110">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="90666-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="90666-111">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90666-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90666-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="90666-112">See also</span></span>

- [<span data-ttu-id="90666-113">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="90666-113">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="90666-114">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="90666-114">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
