---
title: Método ICorDebugThread::GetAppDomain
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetAppDomain
helpviewer_keywords:
- GetAppDomain method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetAppDomain method [.NET Framework debugging]
ms.assetid: 415b3d34-8b35-4b60-a318-140646cc83f8
topic_type:
- apiref
ms.openlocfilehash: a845eed993914e02de34ec5c60ed232ccabc561e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133524"
---
# <a name="icordebugthreadgetappdomain-method"></a><span data-ttu-id="9fada-102">Método ICorDebugThread::GetAppDomain</span><span class="sxs-lookup"><span data-stu-id="9fada-102">ICorDebugThread::GetAppDomain Method</span></span>
<span data-ttu-id="9fada-103">Obtém um ponteiro de interface para o domínio do aplicativo no qual este ICorDebugThread está em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="9fada-103">Gets an interface pointer to the application domain in which this ICorDebugThread is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fada-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9fada-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9fada-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9fada-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="9fada-106">fora Um ponteiro para um objeto ICorDebugAppDomain que representa o domínio do aplicativo no qual esse thread está sendo executado no momento.</span><span class="sxs-lookup"><span data-stu-id="9fada-106">[out] A pointer to an ICorDebugAppDomain object that represents the application domain in which this thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fada-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9fada-107">Requirements</span></span>  
 <span data-ttu-id="9fada-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fada-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fada-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9fada-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9fada-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9fada-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9fada-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fada-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
