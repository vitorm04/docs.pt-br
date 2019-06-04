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
ms.openlocfilehash: 2a28b33f80299ae6fce34f9de66b6f7f1bc70ef6
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490559"
---
# <a name="corexitprocess-function"></a><span data-ttu-id="e8a43-102">Função CorExitProcess</span><span class="sxs-lookup"><span data-stu-id="e8a43-102">CorExitProcess Function</span></span>
<span data-ttu-id="e8a43-103">Desliga o processo não gerenciado atual.</span><span class="sxs-lookup"><span data-stu-id="e8a43-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="e8a43-104">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="e8a43-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="e8a43-105">Use o [iclrmetahost:: Exitprocess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="e8a43-105">Use the [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8a43-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e8a43-106">Syntax</span></span>  
  
```  
void STDMETHODCALLTYPE CorExitProcess (   
  int  exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8a43-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e8a43-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="e8a43-108">Um inteiro que especifica o código de saída do processo.</span><span class="sxs-lookup"><span data-stu-id="e8a43-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8a43-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="e8a43-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e8a43-110">Começando com o .NET Framework 4, `CorExitProcess` sai de cada tempo de execução iniciado no processo, não apenas o tempo de execução ao qual as APIs herdadas tiveram sido associadas.</span><span class="sxs-lookup"><span data-stu-id="e8a43-110">Beginning with the .NET Framework 4, `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8a43-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e8a43-111">Requirements</span></span>  
 <span data-ttu-id="e8a43-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8a43-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8a43-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e8a43-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e8a43-114">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e8a43-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e8a43-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8a43-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8a43-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e8a43-116">See also</span></span>

- [<span data-ttu-id="e8a43-117">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="e8a43-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
