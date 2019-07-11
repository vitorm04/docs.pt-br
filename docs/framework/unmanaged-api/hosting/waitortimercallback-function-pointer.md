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
ms.openlocfilehash: 65af5303468904ee40da4d567381782af70bfb38
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776490"
---
# <a name="waitortimercallback-function-pointer"></a><span data-ttu-id="1280e-102">Ponteiro de função WAITORTIMERCALLBACK</span><span class="sxs-lookup"><span data-stu-id="1280e-102">WAITORTIMERCALLBACK Function Pointer</span></span>
<span data-ttu-id="1280e-103">Aponta para uma função que notifica o host que lidam com uma espera (<xref:System.Threading.WaitHandle>) foi sinalizado ou atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="1280e-103">Points to a function that notifies the host that a wait handle (<xref:System.Threading.WaitHandle>) has either been signaled or timed out.</span></span>  
  
 <span data-ttu-id="1280e-104">Esse ponteiro de função foi preterido no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="1280e-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1280e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1280e-105">Syntax</span></span>  
  
```cpp  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1280e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1280e-106">Parameters</span></span>  
 `lpParameter`  
 <span data-ttu-id="1280e-107">[in] Um ponteiro para um objeto que contém informações definidas pelo host.</span><span class="sxs-lookup"><span data-stu-id="1280e-107">[in] A pointer to an object that contains information defined by the host.</span></span>  
  
 `TimerOrWaitFired`  
 <span data-ttu-id="1280e-108">[in] `true` se o identificador de espera atingiu o tempo limite, ou `false` se ele tiver sido sinalizado.</span><span class="sxs-lookup"><span data-stu-id="1280e-108">[in] `true` if the wait handle timed out, or `false` if it was signaled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1280e-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="1280e-109">Remarks</span></span>  
 <span data-ttu-id="1280e-110">A função à qual `WAITORTIMERCALLBACK` pontos é uma função de retorno de chamada e devem ser implementados pelo gravador do aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="1280e-110">The function to which `WAITORTIMERCALLBACK` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1280e-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1280e-111">Requirements</span></span>  
 <span data-ttu-id="1280e-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1280e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1280e-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1280e-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1280e-114">**Biblioteca:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="1280e-114">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="1280e-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1280e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1280e-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1280e-116">See also</span></span>

- [<span data-ttu-id="1280e-117">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="1280e-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
