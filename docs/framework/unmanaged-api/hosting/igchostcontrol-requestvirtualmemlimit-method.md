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
ms.openlocfilehash: d4814e44b1a5311cf6800c804df7a7e11000cbab
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805143"
---
# <a name="igchostcontrolrequestvirtualmemlimit-method"></a><span data-ttu-id="6c0c1-102">Método IGCHostControl::RequestVirtualMemLimit</span><span class="sxs-lookup"><span data-stu-id="6c0c1-102">IGCHostControl::RequestVirtualMemLimit Method</span></span>
<span data-ttu-id="6c0c1-103">Solicita que o host altere os limites de memória virtual.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-103">Requests the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c0c1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6c0c1-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestVirtualMemLimit (  
    [in] SIZE_T       sztMaxVirtualMemMB,  
    [in, out] SIZE_T* psztNewMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c0c1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6c0c1-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="6c0c1-106">no O tamanho solicitado da memória a ser alocada.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-106">[in] The requested size of memory to be allocated.</span></span>  
  
 `psztNewMaxVirtualMemMB`  
 <span data-ttu-id="6c0c1-107">[entrada, saída] Um ponteiro para o tamanho real da memória alocada.</span><span class="sxs-lookup"><span data-stu-id="6c0c1-107">[in, out] A pointer to the actual size of memory allocated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c0c1-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6c0c1-108">Requirements</span></span>  
 <span data-ttu-id="6c0c1-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c0c1-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c0c1-110">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6c0c1-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6c0c1-111">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6c0c1-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6c0c1-112">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c0c1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c0c1-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="6c0c1-113">See also</span></span>

- [<span data-ttu-id="6c0c1-114">Interface IGCHostControl</span><span class="sxs-lookup"><span data-stu-id="6c0c1-114">IGCHostControl Interface</span></span>](igchostcontrol-interface.md)
