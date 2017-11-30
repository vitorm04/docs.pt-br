---
title: "Função CoEEShutDownCOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CoEEShutDownCOM
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: CoEEShutDownCOM
helpviewer_keywords: CoEEShutDownCOM function [.NET Framework hosting]
ms.assetid: b634cae2-632f-4737-9be4-92d0652844d7
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8d6d9e3d650f65ef084c63104980bca0ac77f1bd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="coeeshutdowncom-function"></a><span data-ttu-id="79d25-102">Função CoEEShutDownCOM</span><span class="sxs-lookup"><span data-stu-id="79d25-102">CoEEShutDownCOM Function</span></span>
<span data-ttu-id="79d25-103">Força o common language runtime (CLR) para liberar todos os ponteiros de interface mantém em runtime callable wrappers (RCW).</span><span class="sxs-lookup"><span data-stu-id="79d25-103">Forces the common language runtime (CLR) to release all interface pointers it holds inside runtime callable wrappers (RCW).</span></span> <span data-ttu-id="79d25-104">Isso tem o efeito de liberar todos os caches RCW.</span><span class="sxs-lookup"><span data-stu-id="79d25-104">This has the effect of releasing all RCW caches.</span></span> <span data-ttu-id="79d25-105">Essa função global foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="79d25-105">This global function is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="79d25-106">Em vez disso, use o ponto de entrada para um tempo de execução específico.</span><span class="sxs-lookup"><span data-stu-id="79d25-106">Instead, use the entry point for a specific runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79d25-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="79d25-107">Syntax</span></span>  
  
```  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="79d25-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="79d25-108">Remarks</span></span>  
 <span data-ttu-id="79d25-109">O `CoEEShutDownCOM` função primeiro libera todos os RCWs em todos os contextos em todos os caches e, em seguida, remove qualquer notificação de desmontagem existente na instalação.</span><span class="sxs-lookup"><span data-stu-id="79d25-109">The `CoEEShutDownCOM` function first releases all the RCWs in all contexts and in all caches, and then removes any tear-down notification existing in setup.</span></span> <span data-ttu-id="79d25-110">Nenhuma DLL descarregar ocorre.</span><span class="sxs-lookup"><span data-stu-id="79d25-110">No DLL unloading occurs.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="79d25-111">Esta função afeta todos os tempos de execução que são carregados no processo.</span><span class="sxs-lookup"><span data-stu-id="79d25-111">This function affects all runtimes that are loaded into the process.</span></span>  
  
 <span data-ttu-id="79d25-112">Começando com o [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], chamar o ponto de entrada para esta função em que o tempo de execução específico que você deseja afetar.</span><span class="sxs-lookup"><span data-stu-id="79d25-112">Beginning with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], call the entry point for this function on the specific runtime you want to affect.</span></span> <span data-ttu-id="79d25-113">Para obter o ponto de entrada, chame o [Iclrruntimeinfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) método e especifique "CoEEShutDownCOM".</span><span class="sxs-lookup"><span data-stu-id="79d25-113">To get the entry point, call the [ICLRRuntimeInfo::GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) method and specify "CoEEShutDownCOM".</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79d25-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="79d25-114">Requirements</span></span>  
 <span data-ttu-id="79d25-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79d25-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79d25-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="79d25-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="79d25-117">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="79d25-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="79d25-118">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79d25-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79d25-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="79d25-119">See Also</span></span>  
 [<span data-ttu-id="79d25-120">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="79d25-120">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
