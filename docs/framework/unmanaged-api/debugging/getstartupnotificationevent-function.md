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
ms.openlocfilehash: 3692471e0652a1a812b1d0cbed9e38cc32112ef4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="getstartupnotificationevent-function"></a><span data-ttu-id="8c463-102">Função GetStartupNotificationEvent</span><span class="sxs-lookup"><span data-stu-id="8c463-102">GetStartupNotificationEvent Function</span></span>
<span data-ttu-id="8c463-103">Cria ou abre um identificador de evento será sinalizado após qualquer common language runtime (CLR) que está sendo carregado no processo de destino especificado.</span><span class="sxs-lookup"><span data-stu-id="8c463-103">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c463-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8c463-104">Syntax</span></span>  
  
```  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8c463-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8c463-105">Parameters</span></span>  
 `debuggeePID`  
 <span data-ttu-id="8c463-106">[in] Identificador de processo do processo de destino do qual deseja receber notificações de inicialização do CLR.</span><span class="sxs-lookup"><span data-stu-id="8c463-106">[in] Process identifier of the target process from which to receive CLR startup notifications.</span></span>  
  
 `phStartupEvent`  
 <span data-ttu-id="8c463-107">[out] Um ponteiro para um identificador que será sinalizado um CLR na inicialização.</span><span class="sxs-lookup"><span data-stu-id="8c463-107">[out] A pointer to a handle that will be signaled by a CLR on startup.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c463-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="8c463-108">Return Value</span></span>  
 <span data-ttu-id="8c463-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="8c463-109">S_OK</span></span>  
 <span data-ttu-id="8c463-110">O identificador para o evento de notificação de inicialização foi obtido com êxito.</span><span class="sxs-lookup"><span data-stu-id="8c463-110">Successfully obtained the handle to the startup notification event.</span></span>  
  
 <span data-ttu-id="8c463-111">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8c463-111">E_INVALIDARG</span></span>  
 <span data-ttu-id="8c463-112">`phStartupEvent` é nulo ou `debuggeePID` não faz referência a um processo que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="8c463-112">`phStartupEvent` is null or `debuggeePID` does not refer to a process that is currently running.</span></span>  
  
 <span data-ttu-id="8c463-113">E_FAIL (ou outros códigos de retorno E_)</span><span class="sxs-lookup"><span data-stu-id="8c463-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="8c463-114">Não é possível obter o identificador para o evento de notificação de inicialização.</span><span class="sxs-lookup"><span data-stu-id="8c463-114">Unable to obtain the handle to the startup notification event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c463-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="8c463-115">Remarks</span></span>  
 <span data-ttu-id="8c463-116">No sistema operacional Windows, `debuggeePID` identificador de processo é mapeado para um sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="8c463-116">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="8c463-117">O evento é sinalizado antes de qualquer gerenciados código é executado pelo CLR que o evento de sinalizado.</span><span class="sxs-lookup"><span data-stu-id="8c463-117">The event is signaled before any managed code is executed by the CLR that signaled the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c463-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8c463-118">Requirements</span></span>  
 <span data-ttu-id="8c463-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c463-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c463-120">**Cabeçalho:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="8c463-120">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="8c463-121">**Biblioteca:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="8c463-121">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="8c463-122">**Versões do .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="8c463-122">**.NET Framework Versions:** 3.5 SP1</span></span>
