---
title: Método IHostMemoryManager::AcquiredVirtualAddressSpace
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.AcquiredVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::AcquiredVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::AcquiredVirtualAddressSpace method [.NET Framework hosting]
- AcquiredVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: ef2f83c2-127e-4c38-8385-306c03cd2167
topic_type:
- apiref
ms.openlocfilehash: f5469a6f35826bcb06fe821e3748861dbf3682f3
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804538"
---
# <a name="ihostmemorymanageracquiredvirtualaddressspace-method"></a><span data-ttu-id="19b9c-102">Método IHostMemoryManager::AcquiredVirtualAddressSpace</span><span class="sxs-lookup"><span data-stu-id="19b9c-102">IHostMemoryManager::AcquiredVirtualAddressSpace Method</span></span>
<span data-ttu-id="19b9c-103">Notifica o host de que o Common Language Runtime (CLR) adquiriu a memória especificada do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="19b9c-103">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19b9c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="19b9c-104">Syntax</span></span>  
  
```cpp  
HRESULT AcquiredVirtualAddressSpace(  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19b9c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="19b9c-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="19b9c-106">no O endereço inicial da memória.</span><span class="sxs-lookup"><span data-stu-id="19b9c-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="19b9c-107">no O tamanho, em bytes, da memória.</span><span class="sxs-lookup"><span data-stu-id="19b9c-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19b9c-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="19b9c-108">Remarks</span></span>  
 <span data-ttu-id="19b9c-109">O `AcquiredVirtualAddressSpace` método é um método de retorno de chamada e deve ser implementado pelo gravador do aplicativo de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="19b9c-109">The `AcquiredVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="19b9c-110">Ele é chamado pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="19b9c-110">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19b9c-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="19b9c-111">Requirements</span></span>  
 <span data-ttu-id="19b9c-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19b9c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19b9c-113">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="19b9c-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="19b9c-114">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="19b9c-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="19b9c-115">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19b9c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19b9c-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="19b9c-116">See also</span></span>

- [<span data-ttu-id="19b9c-117">Interface IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="19b9c-117">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
