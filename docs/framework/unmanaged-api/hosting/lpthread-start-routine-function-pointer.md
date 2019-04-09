---
title: Ponteiro de função LPTHREAD_START_ROUTINE
ms.date: 03/30/2017
api_name:
- LPTHREAD_START_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPTHREAD_START_ROUTINE
helpviewer_keywords:
- LPTHREAD_START_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 7b9b93b0-fe92-42ba-8693-701168a29dde
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 27d1837f9f9f11ad34140f50ec41aa6fe8a62160
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119308"
---
# <a name="lpthreadstartroutine-function-pointer"></a><span data-ttu-id="1d42b-102">Ponteiro de função LPTHREAD_START_ROUTINE</span><span class="sxs-lookup"><span data-stu-id="1d42b-102">LPTHREAD_START_ROUTINE Function Pointer</span></span>
<span data-ttu-id="1d42b-103">Aponta para uma função que notifica o host que um thread começou a executar.</span><span class="sxs-lookup"><span data-stu-id="1d42b-103">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 <span data-ttu-id="1d42b-104">Esse ponteiro de função foi preterido no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1d42b-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d42b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1d42b-105">Syntax</span></span>  
  
```  
typedef DWORD (__stdcall *LPTHREAD_START_ROUTINE) (  
    [in] LPVOID lpThreadParameter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d42b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1d42b-106">Parameters</span></span>  
 `lpThreadParameter`  
 <span data-ttu-id="1d42b-107">[in] Um ponteiro para o código que iniciou a execução.</span><span class="sxs-lookup"><span data-stu-id="1d42b-107">[in] A pointer to the code that has started executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d42b-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="1d42b-108">Remarks</span></span>  
 <span data-ttu-id="1d42b-109">A função à qual `LPTHREAD_START_ROUTINE` pontos é uma função de retorno de chamada e devem ser implementados pelo gravador do aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="1d42b-109">The function to which `LPTHREAD_START_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d42b-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1d42b-110">Requirements</span></span>  
 <span data-ttu-id="1d42b-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d42b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d42b-112">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1d42b-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1d42b-113">**Biblioteca:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="1d42b-113">**Library:** MSCorWks.dll</span></span>  
  
 **<span data-ttu-id="1d42b-114">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="1d42b-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1d42b-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1d42b-115">See also</span></span>

- [<span data-ttu-id="1d42b-116">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="1d42b-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
