---
title: "Função CorExitProcess"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorExitProcess
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: CorExitProcess
helpviewer_keywords: CorExitProcess function [.NET Framework hosting]
ms.assetid: a5cab4c6-990e-47f3-8798-cf422b791015
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 75b35631bad5de46d48ed818c6f929f25a5f7e66
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="corexitprocess-function"></a><span data-ttu-id="a1b1d-102">Função CorExitProcess</span><span class="sxs-lookup"><span data-stu-id="a1b1d-102">CorExitProcess Function</span></span>
<span data-ttu-id="a1b1d-103">Desliga o processo atual de não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a1b1d-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="a1b1d-104">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a1b1d-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="a1b1d-105">Use o [Iclrmetahost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="a1b1d-105">Use the [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1b1d-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a1b1d-106">Syntax</span></span>  
  
```  
void STDMETHODCALLTYPE CorExitProcess (   
  int  exitCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a1b1d-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a1b1d-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="a1b1d-108">Um inteiro que especifica o código de saída do processo.</span><span class="sxs-lookup"><span data-stu-id="a1b1d-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1b1d-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="a1b1d-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a1b1d-110">Começando com o [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], `CorExitProcess` sai cada iniciado tempo de execução do processo, não apenas o tempo de execução para que as APIs herdadas associação.</span><span class="sxs-lookup"><span data-stu-id="a1b1d-110">Beginning with the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1b1d-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a1b1d-111">Requirements</span></span>  
 <span data-ttu-id="a1b1d-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1b1d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1b1d-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a1b1d-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a1b1d-114">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a1b1d-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a1b1d-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1b1d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1b1d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1b1d-116">See Also</span></span>  
 [<span data-ttu-id="a1b1d-117">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="a1b1d-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
