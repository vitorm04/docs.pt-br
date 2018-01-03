---
title: "Função GetStartupNotificationEvent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetStartupNotificationEvent
api_location: dbgshim.dll
api_type: COM
f1_keywords: GetStartupNotificationEvent
helpviewer_keywords:
- GetStartupNotificationEvent function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: c94b1b61-045a-4695-bacd-0f18c5acc246
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 809f34d265e0a1677d8b7fc78515b20df7353968
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="getstartupnotificationevent-function"></a><span data-ttu-id="03327-102">Função GetStartupNotificationEvent</span><span class="sxs-lookup"><span data-stu-id="03327-102">GetStartupNotificationEvent Function</span></span>
<span data-ttu-id="03327-103">Cria ou abre um identificador de evento será sinalizado após qualquer common language runtime (CLR) que está sendo carregado no processo de destino especificado.</span><span class="sxs-lookup"><span data-stu-id="03327-103">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03327-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="03327-104">Syntax</span></span>  
  
```  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="03327-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="03327-105">Parameters</span></span>  
 `debuggeePID`  
 <span data-ttu-id="03327-106">[in] Identificador de processo do processo de destino do qual deseja receber notificações de inicialização do CLR.</span><span class="sxs-lookup"><span data-stu-id="03327-106">[in] Process identifier of the target process from which to receive CLR startup notifications.</span></span>  
  
 `phStartupEvent`  
 <span data-ttu-id="03327-107">[out] Um ponteiro para um identificador que será sinalizado um CLR na inicialização.</span><span class="sxs-lookup"><span data-stu-id="03327-107">[out] A pointer to a handle that will be signaled by a CLR on startup.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03327-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="03327-108">Return Value</span></span>  
 <span data-ttu-id="03327-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="03327-109">S_OK</span></span>  
 <span data-ttu-id="03327-110">O identificador para o evento de notificação de inicialização foi obtido com êxito.</span><span class="sxs-lookup"><span data-stu-id="03327-110">Successfully obtained the handle to the startup notification event.</span></span>  
  
 <span data-ttu-id="03327-111">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="03327-111">E_INVALIDARG</span></span>  
 <span data-ttu-id="03327-112">`phStartupEvent`é nulo ou `debuggeePID` não faz referência a um processo que está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="03327-112">`phStartupEvent` is null or `debuggeePID` does not refer to a process that is currently running.</span></span>  
  
 <span data-ttu-id="03327-113">E_FAIL (ou outros códigos de retorno E_)</span><span class="sxs-lookup"><span data-stu-id="03327-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="03327-114">Não é possível obter o identificador para o evento de notificação de inicialização.</span><span class="sxs-lookup"><span data-stu-id="03327-114">Unable to obtain the handle to the startup notification event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03327-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="03327-115">Remarks</span></span>  
 <span data-ttu-id="03327-116">No sistema operacional Windows, `debuggeePID` identificador de processo é mapeado para um sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="03327-116">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="03327-117">O evento é sinalizado antes de qualquer gerenciados código é executado pelo CLR que o evento de sinalizado.</span><span class="sxs-lookup"><span data-stu-id="03327-117">The event is signaled before any managed code is executed by the CLR that signaled the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03327-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="03327-118">Requirements</span></span>  
 <span data-ttu-id="03327-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03327-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03327-120">**Cabeçalho:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="03327-120">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="03327-121">**Biblioteca:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="03327-121">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="03327-122">**Versões do .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="03327-122">**.NET Framework Versions:** 3.5 SP1</span></span>
