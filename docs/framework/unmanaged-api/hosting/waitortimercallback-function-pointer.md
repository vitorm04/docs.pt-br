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
ms.openlocfilehash: db6a20dee21b6c8bbd55fa9b52a159a00fe310d5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092031"
---
# <a name="waitortimercallback-function-pointer"></a><span data-ttu-id="fff01-102">Ponteiro de função WAITORTIMERCALLBACK</span><span class="sxs-lookup"><span data-stu-id="fff01-102">WAITORTIMERCALLBACK Function Pointer</span></span>
<span data-ttu-id="fff01-103">Aponta para uma função que notifica o host que um identificador de espera (<xref:System.Threading.WaitHandle>) foi sinalizado ou esgotou o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="fff01-103">Points to a function that notifies the host that a wait handle (<xref:System.Threading.WaitHandle>) has either been signaled or timed out.</span></span>  
  
 <span data-ttu-id="fff01-104">Esse ponteiro de função foi preterido no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="fff01-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fff01-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fff01-105">Syntax</span></span>  
  
```cpp  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fff01-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fff01-106">Parameters</span></span>  
 `lpParameter`  
 <span data-ttu-id="fff01-107">no Um ponteiro para um objeto que contém informações definidas pelo host.</span><span class="sxs-lookup"><span data-stu-id="fff01-107">[in] A pointer to an object that contains information defined by the host.</span></span>  
  
 `TimerOrWaitFired`  
 <span data-ttu-id="fff01-108">[in] `true` se o identificador de espera expirou ou `false` se ele foi sinalizado.</span><span class="sxs-lookup"><span data-stu-id="fff01-108">[in] `true` if the wait handle timed out, or `false` if it was signaled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fff01-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="fff01-109">Remarks</span></span>  
 <span data-ttu-id="fff01-110">A função à qual os pontos de `WAITORTIMERCALLBACK` é uma função de retorno de chamada e deve ser implementada pelo gravador do aplicativo de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="fff01-110">The function to which `WAITORTIMERCALLBACK` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fff01-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fff01-111">Requirements</span></span>  
 <span data-ttu-id="fff01-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fff01-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fff01-113">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fff01-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fff01-114">**Biblioteca:** MSCorWks. dll</span><span class="sxs-lookup"><span data-stu-id="fff01-114">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="fff01-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fff01-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fff01-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fff01-116">See also</span></span>

- [<span data-ttu-id="fff01-117">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="fff01-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
