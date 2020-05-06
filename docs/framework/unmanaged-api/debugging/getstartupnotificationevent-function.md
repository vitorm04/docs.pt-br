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
ms.openlocfilehash: 3377dcd5d45ca8e31a57a75bd81366d41837c12c
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860706"
---
# <a name="getstartupnotificationevent-function"></a><span data-ttu-id="41c02-102">Função GetStartupNotificationEvent</span><span class="sxs-lookup"><span data-stu-id="41c02-102">GetStartupNotificationEvent Function</span></span>
<span data-ttu-id="41c02-103">Cria ou abre um identificador de evento que será sinalizado por qualquer Common Language Runtime (CLR) que esteja carregando no processo de destino especificado.</span><span class="sxs-lookup"><span data-stu-id="41c02-103">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41c02-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="41c02-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="41c02-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41c02-105">Parameters</span></span>  
 `debuggeePID`  
 <span data-ttu-id="41c02-106">no Identificador de processo do processo de destino do qual receber notificações de inicialização do CLR.</span><span class="sxs-lookup"><span data-stu-id="41c02-106">[in] Process identifier of the target process from which to receive CLR startup notifications.</span></span>  
  
 `phStartupEvent`  
 <span data-ttu-id="41c02-107">fora Um ponteiro para um identificador que será sinalizado por um CLR na inicialização.</span><span class="sxs-lookup"><span data-stu-id="41c02-107">[out] A pointer to a handle that will be signaled by a CLR on startup.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41c02-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="41c02-108">Return Value</span></span>  
 <span data-ttu-id="41c02-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="41c02-109">S_OK</span></span>  
 <span data-ttu-id="41c02-110">O identificador para o evento de notificação de inicialização foi obtido com êxito.</span><span class="sxs-lookup"><span data-stu-id="41c02-110">Successfully obtained the handle to the startup notification event.</span></span>  
  
 <span data-ttu-id="41c02-111">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="41c02-111">E_INVALIDARG</span></span>  
 <span data-ttu-id="41c02-112">`phStartupEvent`é nulo ou `debuggeePID` não se refere a um processo em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="41c02-112">`phStartupEvent` is null or `debuggeePID` does not refer to a process that is currently running.</span></span>  
  
 <span data-ttu-id="41c02-113">E_FAIL (ou outros códigos de retorno de E_)</span><span class="sxs-lookup"><span data-stu-id="41c02-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="41c02-114">Não é possível obter o identificador para o evento de notificação de inicialização.</span><span class="sxs-lookup"><span data-stu-id="41c02-114">Unable to obtain the handle to the startup notification event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41c02-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="41c02-115">Remarks</span></span>  
 <span data-ttu-id="41c02-116">No sistema operacional Windows, `debuggeePID` o mapeia para um identificador de processo do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="41c02-116">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="41c02-117">O evento é sinalizado antes que qualquer código gerenciado seja executado pelo CLR que sinalizou o evento.</span><span class="sxs-lookup"><span data-stu-id="41c02-117">The event is signaled before any managed code is executed by the CLR that signaled the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41c02-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="41c02-118">Requirements</span></span>  
 <span data-ttu-id="41c02-119">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41c02-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41c02-120">**Cabeçalho:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="41c02-120">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="41c02-121">**Biblioteca:** dbgshim. dll</span><span class="sxs-lookup"><span data-stu-id="41c02-121">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="41c02-122">**Versões do .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="41c02-122">**.NET Framework Versions:** 3.5 SP1</span></span>
