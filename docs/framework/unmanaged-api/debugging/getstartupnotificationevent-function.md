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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ed1db49be78d7d16648a9ef9735e79ef1b3ab98
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487316"
---
# <a name="getstartupnotificationevent-function"></a><span data-ttu-id="df014-102">Função GetStartupNotificationEvent</span><span class="sxs-lookup"><span data-stu-id="df014-102">GetStartupNotificationEvent Function</span></span>
<span data-ttu-id="df014-103">Cria ou abre um identificador de eventos que será sinalizado após qualquer common language runtime (CLR) que está sendo carregada no processo de destino especificado.</span><span class="sxs-lookup"><span data-stu-id="df014-103">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df014-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="df014-104">Syntax</span></span>  
  
```  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="df014-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="df014-105">Parameters</span></span>  
 `debuggeePID`  
 <span data-ttu-id="df014-106">[in] Identificador de processo do processo de destino do qual deseja receber notificações de inicialização do CLR.</span><span class="sxs-lookup"><span data-stu-id="df014-106">[in] Process identifier of the target process from which to receive CLR startup notifications.</span></span>  
  
 `phStartupEvent`  
 <span data-ttu-id="df014-107">[out] Um ponteiro para um identificador que será sinalizado por um CLR na inicialização.</span><span class="sxs-lookup"><span data-stu-id="df014-107">[out] A pointer to a handle that will be signaled by a CLR on startup.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="df014-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="df014-108">Return Value</span></span>  
 <span data-ttu-id="df014-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="df014-109">S_OK</span></span>  
 <span data-ttu-id="df014-110">O identificador para o evento de notificação de inicialização foi obtido com êxito.</span><span class="sxs-lookup"><span data-stu-id="df014-110">Successfully obtained the handle to the startup notification event.</span></span>  
  
 <span data-ttu-id="df014-111">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="df014-111">E_INVALIDARG</span></span>  
 <span data-ttu-id="df014-112">`phStartupEvent` é nulo ou `debuggeePID` não faz referência a um processo que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="df014-112">`phStartupEvent` is null or `debuggeePID` does not refer to a process that is currently running.</span></span>  
  
 <span data-ttu-id="df014-113">E_FAIL (ou outros códigos de retorno e _)</span><span class="sxs-lookup"><span data-stu-id="df014-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="df014-114">Não é possível obter o identificador para o evento de notificação de inicialização.</span><span class="sxs-lookup"><span data-stu-id="df014-114">Unable to obtain the handle to the startup notification event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df014-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="df014-115">Remarks</span></span>  
 <span data-ttu-id="df014-116">No sistema operacional Windows, `debuggeePID` identificador de processo é mapeado para um sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="df014-116">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="df014-117">O evento é sinalizado antes de qualquer gerenciados código é executado pelo CLR que o evento de sinalizado.</span><span class="sxs-lookup"><span data-stu-id="df014-117">The event is signaled before any managed code is executed by the CLR that signaled the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df014-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="df014-118">Requirements</span></span>  
 <span data-ttu-id="df014-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df014-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df014-120">**Cabeçalho:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="df014-120">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="df014-121">**Biblioteca:** dbgshim</span><span class="sxs-lookup"><span data-stu-id="df014-121">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="df014-122">**Versões do .NET framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="df014-122">**.NET Framework Versions:** 3.5 SP1</span></span>
