---
title: Ponteiro de função WAITORTIMERCALLBACK
ms.date: 03/30/2017
api_name:
- WAITORTIMERCALLBACK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAITORTIMERCALLBACK
helpviewer_keywords:
- WAITORTIMERCALLBACK function pointer [.NET Framework hosting]
ms.assetid: 1fec4aef-0a06-4df0-bae7-d31a9ef9603d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24a2c3baec0d958302101c295966f945ae98fa78
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490704"
---
# <a name="waitortimercallback-function-pointer"></a><span data-ttu-id="bf307-102">Ponteiro de função WAITORTIMERCALLBACK</span><span class="sxs-lookup"><span data-stu-id="bf307-102">WAITORTIMERCALLBACK Function Pointer</span></span>
<span data-ttu-id="bf307-103">Aponta para uma função que notifica o host que lidam com uma espera (<xref:System.Threading.WaitHandle>) foi sinalizado ou atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="bf307-103">Points to a function that notifies the host that a wait handle (<xref:System.Threading.WaitHandle>) has either been signaled or timed out.</span></span>  
  
 <span data-ttu-id="bf307-104">Esse ponteiro de função foi preterido no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bf307-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf307-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bf307-105">Syntax</span></span>  
  
```  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf307-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bf307-106">Parameters</span></span>  
 `lpParameter`  
 <span data-ttu-id="bf307-107">[in] Um ponteiro para um objeto que contém informações definidas pelo host.</span><span class="sxs-lookup"><span data-stu-id="bf307-107">[in] A pointer to an object that contains information defined by the host.</span></span>  
  
 `TimerOrWaitFired`  
 <span data-ttu-id="bf307-108">[in] `true` se o identificador de espera atingiu o tempo limite, ou `false` se ele tiver sido sinalizado.</span><span class="sxs-lookup"><span data-stu-id="bf307-108">[in] `true` if the wait handle timed out, or `false` if it was signaled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf307-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="bf307-109">Remarks</span></span>  
 <span data-ttu-id="bf307-110">A função à qual `WAITORTIMERCALLBACK` pontos é uma função de retorno de chamada e devem ser implementados pelo gravador do aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="bf307-110">The function to which `WAITORTIMERCALLBACK` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf307-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bf307-111">Requirements</span></span>  
 <span data-ttu-id="bf307-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf307-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf307-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bf307-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bf307-114">**Biblioteca:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="bf307-114">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="bf307-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf307-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf307-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf307-116">See also</span></span>
- [<span data-ttu-id="bf307-117">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="bf307-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
