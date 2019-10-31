---
title: Método IGCHostControl::RequestVirtualMemLimit
ms.date: 03/30/2017
api_name:
- IGCHostControl.RequestVirtualMemLimit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- RequestVirtualMemLimit
helpviewer_keywords:
- IGCHostControl::RequestVirtualMemLimit method [.NET Framework hosting]
- RequestVirtualMemLimit method [.NET Framework hosting]
ms.assetid: f4984a8c-4c0e-4460-9aa1-d022b3621228
topic_type:
- apiref
ms.openlocfilehash: ccff575974093de0bf00b257cba78c509f9cbd92
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134770"
---
# <a name="igchostcontrolrequestvirtualmemlimit-method"></a><span data-ttu-id="8f798-102">Método IGCHostControl::RequestVirtualMemLimit</span><span class="sxs-lookup"><span data-stu-id="8f798-102">IGCHostControl::RequestVirtualMemLimit Method</span></span>
<span data-ttu-id="8f798-103">Solicita que o host altere os limites de memória virtual.</span><span class="sxs-lookup"><span data-stu-id="8f798-103">Requests the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f798-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8f798-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestVirtualMemLimit (  
    [in] SIZE_T       sztMaxVirtualMemMB,  
    [in, out] SIZE_T* psztNewMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f798-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8f798-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="8f798-106">no O tamanho solicitado da memória a ser alocada.</span><span class="sxs-lookup"><span data-stu-id="8f798-106">[in] The requested size of memory to be allocated.</span></span>  
  
 `psztNewMaxVirtualMemMB`  
 <span data-ttu-id="8f798-107">[entrada, saída] Um ponteiro para o tamanho real da memória alocada.</span><span class="sxs-lookup"><span data-stu-id="8f798-107">[in, out] A pointer to the actual size of memory allocated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f798-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8f798-108">Requirements</span></span>  
 <span data-ttu-id="8f798-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f798-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f798-110">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8f798-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8f798-111">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8f798-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8f798-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f798-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f798-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8f798-113">See also</span></span>

- [<span data-ttu-id="8f798-114">Interface IGCHostControl</span><span class="sxs-lookup"><span data-stu-id="8f798-114">IGCHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)
