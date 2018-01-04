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
ms.workload: dotnet
ms.openlocfilehash: 560f63c131ad336a3ff4b4edec0aed2b58d33ba5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="corexitprocess-function"></a><span data-ttu-id="8d954-102">Função CorExitProcess</span><span class="sxs-lookup"><span data-stu-id="8d954-102">CorExitProcess Function</span></span>
<span data-ttu-id="8d954-103">Desliga o processo atual de não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8d954-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="8d954-104">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8d954-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="8d954-105">Use o [Iclrmetahost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="8d954-105">Use the [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d954-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8d954-106">Syntax</span></span>  
  
```  
void STDMETHODCALLTYPE CorExitProcess (   
  int  exitCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8d954-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8d954-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="8d954-108">Um inteiro que especifica o código de saída do processo.</span><span class="sxs-lookup"><span data-stu-id="8d954-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d954-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="8d954-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d954-110">Começando com o [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], `CorExitProcess` sai cada iniciado tempo de execução do processo, não apenas o tempo de execução para que as APIs herdadas associação.</span><span class="sxs-lookup"><span data-stu-id="8d954-110">Beginning with the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d954-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8d954-111">Requirements</span></span>  
 <span data-ttu-id="8d954-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d954-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d954-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8d954-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8d954-114">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8d954-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8d954-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d954-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d954-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d954-116">See Also</span></span>  
 [<span data-ttu-id="8d954-117">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="8d954-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
