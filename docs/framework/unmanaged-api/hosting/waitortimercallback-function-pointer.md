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
ms.openlocfilehash: 1d36ae3ef63c1324f77786ad55674bbdc257d984
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607128"
---
# <a name="waitortimercallback-function-pointer"></a><span data-ttu-id="8c707-102">Ponteiro de função WAITORTIMERCALLBACK</span><span class="sxs-lookup"><span data-stu-id="8c707-102">WAITORTIMERCALLBACK Function Pointer</span></span>
<span data-ttu-id="8c707-103">Aponta para uma função que notifica o host que lidam com uma espera (<xref:System.Threading.WaitHandle>) foi sinalizado ou atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="8c707-103">Points to a function that notifies the host that a wait handle (<xref:System.Threading.WaitHandle>) has either been signaled or timed out.</span></span>  
  
 <span data-ttu-id="8c707-104">Esse ponteiro de função foi preterido no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8c707-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c707-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8c707-105">Syntax</span></span>  
  
```  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8c707-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8c707-106">Parameters</span></span>  
 `lpParameter`  
 <span data-ttu-id="8c707-107">[in] Um ponteiro para um objeto que contém informações definidas pelo host.</span><span class="sxs-lookup"><span data-stu-id="8c707-107">[in] A pointer to an object that contains information defined by the host.</span></span>  
  
 `TimerOrWaitFired`  
 <span data-ttu-id="8c707-108">[in] `true` se o identificador de espera atingiu o tempo limite, ou `false` se ele tiver sido sinalizado.</span><span class="sxs-lookup"><span data-stu-id="8c707-108">[in] `true` if the wait handle timed out, or `false` if it was signaled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c707-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="8c707-109">Remarks</span></span>  
 <span data-ttu-id="8c707-110">A função à qual `WAITORTIMERCALLBACK` pontos é uma função de retorno de chamada e devem ser implementados pelo gravador do aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="8c707-110">The function to which `WAITORTIMERCALLBACK` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c707-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8c707-111">Requirements</span></span>  
 <span data-ttu-id="8c707-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c707-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c707-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8c707-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8c707-114">**Biblioteca:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="8c707-114">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="8c707-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c707-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c707-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8c707-116">See also</span></span>
- [<span data-ttu-id="8c707-117">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="8c707-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
