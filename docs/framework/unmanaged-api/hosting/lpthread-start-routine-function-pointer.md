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
ms.openlocfilehash: 5025b75106b2cb0853047a09ca263f795d99633f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441173"
---
# <a name="lpthreadstartroutine-function-pointer"></a><span data-ttu-id="8a3d1-102">Ponteiro de função LPTHREAD_START_ROUTINE</span><span class="sxs-lookup"><span data-stu-id="8a3d1-102">LPTHREAD_START_ROUTINE Function Pointer</span></span>
<span data-ttu-id="8a3d1-103">Aponta para uma função que notifica o host que um thread começou a executar.</span><span class="sxs-lookup"><span data-stu-id="8a3d1-103">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 <span data-ttu-id="8a3d1-104">Este ponteiro de função foi preterido no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8a3d1-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a3d1-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8a3d1-105">Syntax</span></span>  
  
```  
typedef DWORD (__stdcall *LPTHREAD_START_ROUTINE) (  
    [in] LPVOID lpThreadParameter  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8a3d1-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8a3d1-106">Parameters</span></span>  
 `lpThreadParameter`  
 <span data-ttu-id="8a3d1-107">[in] Um ponteiro para o código que iniciou a execução.</span><span class="sxs-lookup"><span data-stu-id="8a3d1-107">[in] A pointer to the code that has started executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a3d1-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="8a3d1-108">Remarks</span></span>  
 <span data-ttu-id="8a3d1-109">A função à qual `LPTHREAD_START_ROUTINE` pontos é uma função de retorno de chamada e devem ser implementados pelo gravador do aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="8a3d1-109">The function to which `LPTHREAD_START_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a3d1-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8a3d1-110">Requirements</span></span>  
 <span data-ttu-id="8a3d1-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a3d1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a3d1-112">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8a3d1-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8a3d1-113">**Biblioteca:** arquivo MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="8a3d1-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="8a3d1-114">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a3d1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a3d1-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a3d1-115">See Also</span></span>  
 [<span data-ttu-id="8a3d1-116">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="8a3d1-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
