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
ms.openlocfilehash: 1aea017f17e29544e9288e1f57e6f84f9a2f6dae
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501099"
---
# <a name="imetadatatablesgetuserstringheapsize-method"></a><span data-ttu-id="201b9-102">Método IMetaDataTables::GetUserStringHeapSize</span><span class="sxs-lookup"><span data-stu-id="201b9-102">IMetaDataTables::GetUserStringHeapSize Method</span></span>
<span data-ttu-id="201b9-103">Obtém o tamanho, em bytes, do heap de cadeia de caracteres do usuário.</span><span class="sxs-lookup"><span data-stu-id="201b9-103">Gets the size, in bytes, of the user string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="201b9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="201b9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserStringHeapSize (  
    [out] ULONG   *pcbBlobs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="201b9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="201b9-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="201b9-106">fora Um ponteiro para o tamanho, em bytes, do heap de cadeia de caracteres do usuário.</span><span class="sxs-lookup"><span data-stu-id="201b9-106">[out] A pointer to the size, in bytes, of the user string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="201b9-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="201b9-107">Requirements</span></span>  
 <span data-ttu-id="201b9-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="201b9-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="201b9-109">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="201b9-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="201b9-110">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="201b9-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="201b9-111">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="201b9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="201b9-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="201b9-112">See also</span></span>

- [<span data-ttu-id="201b9-113">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="201b9-113">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="201b9-114">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="201b9-114">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
