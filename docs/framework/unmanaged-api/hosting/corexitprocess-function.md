---
title: Função CorExitProcess
ms.date: 03/30/2017
api_name:
- CorExitProcess
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CorExitProcess
helpviewer_keywords:
- CorExitProcess function [.NET Framework hosting]
ms.assetid: a5cab4c6-990e-47f3-8798-cf422b791015
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a93e73fa8345b48e604d6f63d16170d850ead451
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484570"
---
# <a name="corexitprocess-function"></a><span data-ttu-id="aa82a-102">Função CorExitProcess</span><span class="sxs-lookup"><span data-stu-id="aa82a-102">CorExitProcess Function</span></span>
<span data-ttu-id="aa82a-103">Desliga o processo não gerenciado atual.</span><span class="sxs-lookup"><span data-stu-id="aa82a-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="aa82a-104">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="aa82a-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="aa82a-105">Use o [iclrmetahost:: Exitprocess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="aa82a-105">Use the [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa82a-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aa82a-106">Syntax</span></span>  
  
```  
void STDMETHODCALLTYPE CorExitProcess (   
  int  exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa82a-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="aa82a-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="aa82a-108">Um inteiro que especifica o código de saída do processo.</span><span class="sxs-lookup"><span data-stu-id="aa82a-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa82a-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="aa82a-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa82a-110">Começando com o [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], `CorExitProcess` sai de cada tempo de execução iniciado no processo, não apenas o tempo de execução ao qual as APIs herdadas tiveram sido associadas.</span><span class="sxs-lookup"><span data-stu-id="aa82a-110">Beginning with the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa82a-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aa82a-111">Requirements</span></span>  
 <span data-ttu-id="aa82a-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa82a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa82a-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="aa82a-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aa82a-114">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aa82a-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aa82a-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa82a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa82a-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa82a-116">See also</span></span>
- [<span data-ttu-id="aa82a-117">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="aa82a-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
