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
ms.openlocfilehash: ce8d3356b1f9b73e33ed2d3215c7f8115e64ac70
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426643"
---
# <a name="imetadatatablesgetuserstringheapsize-method"></a><span data-ttu-id="8ef17-102">Método IMetaDataTables::GetUserStringHeapSize</span><span class="sxs-lookup"><span data-stu-id="8ef17-102">IMetaDataTables::GetUserStringHeapSize Method</span></span>
<span data-ttu-id="8ef17-103">Obtém o tamanho, em bytes, do heap de cadeia de caracteres do usuário.</span><span class="sxs-lookup"><span data-stu-id="8ef17-103">Gets the size, in bytes, of the user string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ef17-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8ef17-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserStringHeapSize (  
    [out] ULONG   *pcbBlobs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ef17-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8ef17-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="8ef17-106">fora Um ponteiro para o tamanho, em bytes, do heap de cadeia de caracteres do usuário.</span><span class="sxs-lookup"><span data-stu-id="8ef17-106">[out] A pointer to the size, in bytes, of the user string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ef17-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8ef17-107">Requirements</span></span>  
 <span data-ttu-id="8ef17-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ef17-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ef17-109">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8ef17-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8ef17-110">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8ef17-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8ef17-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ef17-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ef17-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ef17-112">See also</span></span>

- [<span data-ttu-id="8ef17-113">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="8ef17-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="8ef17-114">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="8ef17-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
