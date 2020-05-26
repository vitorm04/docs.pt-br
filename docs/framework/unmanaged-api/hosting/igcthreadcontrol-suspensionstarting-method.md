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
ms.openlocfilehash: 2acabe66e3b6b5652df20e31a9d2294c2396b54b
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805097"
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a><span data-ttu-id="b7dbe-102">Método IGCThreadControl::SuspensionStarting</span><span class="sxs-lookup"><span data-stu-id="b7dbe-102">IGCThreadControl::SuspensionStarting Method</span></span>
<span data-ttu-id="b7dbe-103">Notifica o host de que o tempo de execução está começando uma suspensão de thread para uma coleta de lixo ou outra suspensão.</span><span class="sxs-lookup"><span data-stu-id="b7dbe-103">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7dbe-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7dbe-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="b7dbe-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="b7dbe-105">Remarks</span></span>  
 <span data-ttu-id="b7dbe-106">Não reagende nenhum thread durante o `SuspensionStarting` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="b7dbe-106">Do not reschedule any threads during the `SuspensionStarting` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7dbe-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b7dbe-107">Requirements</span></span>  
 <span data-ttu-id="b7dbe-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7dbe-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7dbe-109">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b7dbe-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b7dbe-110">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b7dbe-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b7dbe-111">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7dbe-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7dbe-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="b7dbe-112">See also</span></span>

- [<span data-ttu-id="b7dbe-113">Interface IGCThreadControl</span><span class="sxs-lookup"><span data-stu-id="b7dbe-113">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)
