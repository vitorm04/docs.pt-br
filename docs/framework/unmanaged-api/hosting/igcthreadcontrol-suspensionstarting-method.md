---
title: Método IGCThreadControl::SuspensionStarting
ms.date: 03/30/2017
api_name:
- IGCThreadControl.SuspensionStarting
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SuspensionStarting
helpviewer_keywords:
- IGCThreadControl::SuspensionStarting method [.NET Framework hosting]
- SuspensionStarting method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 0af312af-98e9-415e-b182-42e80a1aee51
topic_type:
- apiref
ms.openlocfilehash: 1e1d63ab28276f69e5b3a762520db8f8300d05bc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134756"
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a><span data-ttu-id="31fd9-102">Método IGCThreadControl::SuspensionStarting</span><span class="sxs-lookup"><span data-stu-id="31fd9-102">IGCThreadControl::SuspensionStarting Method</span></span>
<span data-ttu-id="31fd9-103">Notifica o host de que o tempo de execução está começando uma suspensão de thread para uma coleta de lixo ou outra suspensão.</span><span class="sxs-lookup"><span data-stu-id="31fd9-103">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31fd9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="31fd9-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="31fd9-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="31fd9-105">Remarks</span></span>  
 <span data-ttu-id="31fd9-106">Não reagende nenhum thread durante o retorno de chamada `SuspensionStarting`.</span><span class="sxs-lookup"><span data-stu-id="31fd9-106">Do not reschedule any threads during the `SuspensionStarting` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31fd9-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="31fd9-107">Requirements</span></span>  
 <span data-ttu-id="31fd9-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31fd9-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31fd9-109">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="31fd9-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="31fd9-110">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="31fd9-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="31fd9-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31fd9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31fd9-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="31fd9-112">See also</span></span>

- [<span data-ttu-id="31fd9-113">Interface IGCThreadControl</span><span class="sxs-lookup"><span data-stu-id="31fd9-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
