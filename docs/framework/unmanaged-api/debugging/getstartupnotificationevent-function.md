---
title: Função GetStartupNotificationEvent
ms.date: 03/30/2017
api_name:
- GetStartupNotificationEvent
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- GetStartupNotificationEvent
helpviewer_keywords:
- GetStartupNotificationEvent function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: c94b1b61-045a-4695-bacd-0f18c5acc246
topic_type:
- apiref
ms.openlocfilehash: fb158b35165fb229fc78169e2508679b6749752e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122945"
---
# <a name="getstartupnotificationevent-function"></a><span data-ttu-id="ea48d-102">Função GetStartupNotificationEvent</span><span class="sxs-lookup"><span data-stu-id="ea48d-102">GetStartupNotificationEvent Function</span></span>
<span data-ttu-id="ea48d-103">Cria ou abre um identificador de evento que será sinalizado por qualquer Common Language Runtime (CLR) que esteja carregando no processo de destino especificado.</span><span class="sxs-lookup"><span data-stu-id="ea48d-103">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea48d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ea48d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea48d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ea48d-105">Parameters</span></span>  
 `debuggeePID`  
 <span data-ttu-id="ea48d-106">no Identificador de processo do processo de destino do qual receber notificações de inicialização do CLR.</span><span class="sxs-lookup"><span data-stu-id="ea48d-106">[in] Process identifier of the target process from which to receive CLR startup notifications.</span></span>  
  
 `phStartupEvent`  
 <span data-ttu-id="ea48d-107">fora Um ponteiro para um identificador que será sinalizado por um CLR na inicialização.</span><span class="sxs-lookup"><span data-stu-id="ea48d-107">[out] A pointer to a handle that will be signaled by a CLR on startup.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ea48d-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="ea48d-108">Return Value</span></span>  
 <span data-ttu-id="ea48d-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="ea48d-109">S_OK</span></span>  
 <span data-ttu-id="ea48d-110">O identificador para o evento de notificação de inicialização foi obtido com êxito.</span><span class="sxs-lookup"><span data-stu-id="ea48d-110">Successfully obtained the handle to the startup notification event.</span></span>  
  
 <span data-ttu-id="ea48d-111">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ea48d-111">E_INVALIDARG</span></span>  
 <span data-ttu-id="ea48d-112">`phStartupEvent` é nulo ou `debuggeePID` não se refere a um processo em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="ea48d-112">`phStartupEvent` is null or `debuggeePID` does not refer to a process that is currently running.</span></span>  
  
 <span data-ttu-id="ea48d-113">E_FAIL (ou outros códigos de retorno de E_)</span><span class="sxs-lookup"><span data-stu-id="ea48d-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="ea48d-114">Não é possível obter o identificador para o evento de notificação de inicialização.</span><span class="sxs-lookup"><span data-stu-id="ea48d-114">Unable to obtain the handle to the startup notification event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea48d-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="ea48d-115">Remarks</span></span>  
 <span data-ttu-id="ea48d-116">No sistema operacional Windows, o `debuggeePID` é mapeado para um identificador de processo do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="ea48d-116">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="ea48d-117">O evento é sinalizado antes que qualquer código gerenciado seja executado pelo CLR que sinalizou o evento.</span><span class="sxs-lookup"><span data-stu-id="ea48d-117">The event is signaled before any managed code is executed by the CLR that signaled the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea48d-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ea48d-118">Requirements</span></span>  
 <span data-ttu-id="ea48d-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea48d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea48d-120">**Cabeçalho:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="ea48d-120">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="ea48d-121">**Biblioteca:** dbgshim. dll</span><span class="sxs-lookup"><span data-stu-id="ea48d-121">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="ea48d-122">**Versões do .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="ea48d-122">**.NET Framework Versions:** 3.5 SP1</span></span>
