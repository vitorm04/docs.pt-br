---
title: Método ICorConfiguration::SetDebuggerThreadControl
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetDebuggerThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetDebuggerThreadControl
helpviewer_keywords:
- SetDebuggerThreadControl method [.NET Framework hosting]
- ICorConfiguration::SetDebuggerThreadControl method [.NET Framework hosting]
ms.assetid: 1ded7639-dacb-4db1-961c-d1ceaec01959
topic_type:
- apiref
ms.openlocfilehash: d02b834b22ba7897e4939de88bc3c61c62ac2b0e
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762403"
---
# <a name="icorconfigurationsetdebuggerthreadcontrol-method"></a><span data-ttu-id="cb648-102">Método ICorConfiguration::SetDebuggerThreadControl</span><span class="sxs-lookup"><span data-stu-id="cb648-102">ICorConfiguration::SetDebuggerThreadControl Method</span></span>
<span data-ttu-id="cb648-103">Define a interface de retorno de chamada que os serviços de depuração chamarão à medida que os threads Common Language Runtime (CLR) são bloqueados e desbloqueados para depuração.</span><span class="sxs-lookup"><span data-stu-id="cb648-103">Sets the callback interface that the debugging services will call as common language runtime (CLR) threads are blocked and unblocked for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb648-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cb648-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDebuggerThreadControl (  
    [in] IDebuggerThreadControl* pDebuggerThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb648-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cb648-105">Parameters</span></span>  
 `pDebuggerThreadControl`  
 <span data-ttu-id="cb648-106">no Um ponteiro para um objeto [IDebuggerThreadControl](idebuggerthreadcontrol-interface.md) que notifica o host sobre o bloqueio e o desbloqueio de threads pelos serviços de depuração.</span><span class="sxs-lookup"><span data-stu-id="cb648-106">[in] A pointer to an [IDebuggerThreadControl](idebuggerthreadcontrol-interface.md) object that notifies the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb648-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cb648-107">Requirements</span></span>  
 <span data-ttu-id="cb648-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb648-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb648-109">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cb648-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cb648-110">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cb648-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cb648-111">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb648-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb648-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="cb648-112">See also</span></span>

- [<span data-ttu-id="cb648-113">Interface ICorConfiguration</span><span class="sxs-lookup"><span data-stu-id="cb648-113">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)
