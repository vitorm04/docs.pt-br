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
ms.openlocfilehash: 44578595b3cb790570c5359e714bd39c109cf1f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176455"
---
# <a name="corexitprocess-function"></a><span data-ttu-id="08b15-102">Função CorExitProcess</span><span class="sxs-lookup"><span data-stu-id="08b15-102">CorExitProcess Function</span></span>
<span data-ttu-id="08b15-103">Encerra o processo não gerenciado atual.</span><span class="sxs-lookup"><span data-stu-id="08b15-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="08b15-104">Esta função foi depreciada no Quadro .NET 4.</span><span class="sxs-lookup"><span data-stu-id="08b15-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="08b15-105">Use o método [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="08b15-105">Use the [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08b15-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="08b15-106">Syntax</span></span>  
  
```cpp  
void STDMETHODCALLTYPE CorExitProcess (
  int  exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08b15-107">parâmetros</span><span class="sxs-lookup"><span data-stu-id="08b15-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="08b15-108">Um inteiro que especifica o código de saída do processo.</span><span class="sxs-lookup"><span data-stu-id="08b15-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08b15-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="08b15-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="08b15-110">Começando com o .NET `CorExitProcess` Framework 4, as saídas de todo tempo de execução iniciado no processo, não apenas o tempo de execução ao qual as APIs herdadas foram vinculadas.</span><span class="sxs-lookup"><span data-stu-id="08b15-110">Beginning with the .NET Framework 4, `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08b15-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="08b15-111">Requirements</span></span>  
 <span data-ttu-id="08b15-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08b15-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08b15-113">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="08b15-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="08b15-114">**Biblioteca:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="08b15-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="08b15-115">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08b15-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08b15-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="08b15-116">See also</span></span>

- [<span data-ttu-id="08b15-117">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="08b15-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
