---
title: Método ICorConfiguration::SetGCHostControl
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetGCHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCHostControl
helpviewer_keywords:
- ICorConfiguration::SetGCHostControl method [.NET Framework hosting]
- SetGCHostControl method [.NET Framework hosting]
ms.assetid: bca6bd79-e288-475a-aa46-6bf81541d966
topic_type:
- apiref
ms.openlocfilehash: 5a32fb0480e76f47495590a29c329f54722e2dee
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127776"
---
# <a name="icorconfigurationsetgchostcontrol-method"></a><span data-ttu-id="31185-102">Método ICorConfiguration::SetGCHostControl</span><span class="sxs-lookup"><span data-stu-id="31185-102">ICorConfiguration::SetGCHostControl Method</span></span>
<span data-ttu-id="31185-103">Define a interface de retorno de chamada a ser usada pelo coletor de lixo para solicitar que o host altere os limites de memória virtual.</span><span class="sxs-lookup"><span data-stu-id="31185-103">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31185-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="31185-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCHostControl (  
    [in] IGCHostControl* pGCHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31185-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="31185-105">Parameters</span></span>  
 `pGCHostControl`  
 <span data-ttu-id="31185-106">no Um ponteiro para um objeto [IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) que permite que o coletor de lixo solicite o host para alterar os limites de memória virtual.</span><span class="sxs-lookup"><span data-stu-id="31185-106">[in] A pointer to an [IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) object that allows the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31185-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="31185-107">Requirements</span></span>  
 <span data-ttu-id="31185-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31185-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31185-109">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="31185-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="31185-110">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="31185-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="31185-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31185-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31185-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="31185-112">See also</span></span>

- [<span data-ttu-id="31185-113">Interface ICorConfiguration</span><span class="sxs-lookup"><span data-stu-id="31185-113">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
