---
title: Método IHostMemoryManager::NeedsVirtualAddressSpace
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.NeedsVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace method [.NET Framework hosting]
- NeedsVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: 71f0eab5-0170-46f8-9f88-1df5abdeb34a
topic_type:
- apiref
ms.openlocfilehash: bb13c7329c558aa92ec65237aa8a9963c82fe1dc
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804521"
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a><span data-ttu-id="5f5db-102">Método IHostMemoryManager::NeedsVirtualAddressSpace</span><span class="sxs-lookup"><span data-stu-id="5f5db-102">IHostMemoryManager::NeedsVirtualAddressSpace Method</span></span>
<span data-ttu-id="5f5db-103">Notifica o host de que o Common Language Runtime (CLR) tentará usar a memória especificada.</span><span class="sxs-lookup"><span data-stu-id="5f5db-103">Notifies the host that the common language runtime (CLR) is going to attempt to use the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f5db-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5f5db-104">Syntax</span></span>  
  
```cpp  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f5db-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5f5db-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="5f5db-106">no O endereço inicial da memória.</span><span class="sxs-lookup"><span data-stu-id="5f5db-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="5f5db-107">no O tamanho, em bytes, da memória.</span><span class="sxs-lookup"><span data-stu-id="5f5db-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f5db-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="5f5db-108">Remarks</span></span>  
 <span data-ttu-id="5f5db-109">O `NeedsVirtualAddressSpace` método é um método de retorno de chamada e deve ser implementado pelo gravador do aplicativo de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="5f5db-109">The `NeedsVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="5f5db-110">Ele é chamado pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="5f5db-110">It is called by the CLR.</span></span>  
  
 <span data-ttu-id="5f5db-111">Se o host não quiser que o CLR use a memória especificada, ele poderá retornar um E_OUTOFMEMORY HRESULT.</span><span class="sxs-lookup"><span data-stu-id="5f5db-111">If the host does not want the CLR to use the specified memory, it may return an E_OUTOFMEMORY HRESULT.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f5db-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5f5db-112">Requirements</span></span>  
 <span data-ttu-id="5f5db-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f5db-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f5db-114">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5f5db-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5f5db-115">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5f5db-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5f5db-116">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f5db-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f5db-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="5f5db-117">See also</span></span>

- [<span data-ttu-id="5f5db-118">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="5f5db-118">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
