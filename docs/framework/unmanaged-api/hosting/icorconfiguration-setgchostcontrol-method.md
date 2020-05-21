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
ms.openlocfilehash: e648b36a2b276d9335eefaf71b57ad76f9fe0def
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762377"
---
# <a name="icorconfigurationsetgchostcontrol-method"></a><span data-ttu-id="10c00-102">Método ICorConfiguration::SetGCHostControl</span><span class="sxs-lookup"><span data-stu-id="10c00-102">ICorConfiguration::SetGCHostControl Method</span></span>
<span data-ttu-id="10c00-103">Define a interface de retorno de chamada a ser usada pelo coletor de lixo para solicitar que o host altere os limites de memória virtual.</span><span class="sxs-lookup"><span data-stu-id="10c00-103">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10c00-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="10c00-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCHostControl (  
    [in] IGCHostControl* pGCHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10c00-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="10c00-105">Parameters</span></span>  
 `pGCHostControl`  
 <span data-ttu-id="10c00-106">no Um ponteiro para um objeto [IGCHostControl](igchostcontrol-interface.md) que permite que o coletor de lixo solicite o host para alterar os limites de memória virtual.</span><span class="sxs-lookup"><span data-stu-id="10c00-106">[in] A pointer to an [IGCHostControl](igchostcontrol-interface.md) object that allows the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10c00-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="10c00-107">Requirements</span></span>  
 <span data-ttu-id="10c00-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10c00-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10c00-109">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="10c00-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="10c00-110">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="10c00-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="10c00-111">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10c00-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10c00-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="10c00-112">See also</span></span>

- [<span data-ttu-id="10c00-113">Interface ICorConfiguration</span><span class="sxs-lookup"><span data-stu-id="10c00-113">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)
