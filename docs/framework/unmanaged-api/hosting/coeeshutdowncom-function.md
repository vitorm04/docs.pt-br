---
title: Função CoEEShutDownCOM
ms.date: 03/30/2017
api_name:
- CoEEShutDownCOM
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoEEShutDownCOM
helpviewer_keywords:
- CoEEShutDownCOM function [.NET Framework hosting]
ms.assetid: b634cae2-632f-4737-9be4-92d0652844d7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d990d63a007240ab0bd0240f7b45fed52e2a2129
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212242"
---
# <a name="coeeshutdowncom-function"></a><span data-ttu-id="1a708-102">Função CoEEShutDownCOM</span><span class="sxs-lookup"><span data-stu-id="1a708-102">CoEEShutDownCOM Function</span></span>
<span data-ttu-id="1a708-103">Força o common language runtime (CLR) para liberar todos os ponteiros de interface, que ele mantém dentro do runtime callable wrappers (RCW).</span><span class="sxs-lookup"><span data-stu-id="1a708-103">Forces the common language runtime (CLR) to release all interface pointers it holds inside runtime callable wrappers (RCW).</span></span> <span data-ttu-id="1a708-104">Isso tem o efeito de liberar todos os caches RCW.</span><span class="sxs-lookup"><span data-stu-id="1a708-104">This has the effect of releasing all RCW caches.</span></span> <span data-ttu-id="1a708-105">Essa função global foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1a708-105">This global function is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="1a708-106">Em vez disso, use o ponto de entrada para um tempo de execução específico.</span><span class="sxs-lookup"><span data-stu-id="1a708-106">Instead, use the entry point for a specific runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a708-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1a708-107">Syntax</span></span>  
  
```  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="1a708-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="1a708-108">Remarks</span></span>  
 <span data-ttu-id="1a708-109">O `CoEEShutDownCOM` função primeiro libera todos os RCWs em todos os contextos e em todos os caches e, em seguida, remove qualquer notificação de desmontagem existente na instalação.</span><span class="sxs-lookup"><span data-stu-id="1a708-109">The `CoEEShutDownCOM` function first releases all the RCWs in all contexts and in all caches, and then removes any tear-down notification existing in setup.</span></span> <span data-ttu-id="1a708-110">Nenhuma DLL descarregando ocorre.</span><span class="sxs-lookup"><span data-stu-id="1a708-110">No DLL unloading occurs.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="1a708-111">Esta função afeta todos os tempos de execução que são carregados no processo.</span><span class="sxs-lookup"><span data-stu-id="1a708-111">This function affects all runtimes that are loaded into the process.</span></span>  
  
 <span data-ttu-id="1a708-112">Começando com o [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], chamar o ponto de entrada para esta função em que o tempo de execução específico que você deseja afetar.</span><span class="sxs-lookup"><span data-stu-id="1a708-112">Beginning with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], call the entry point for this function on the specific runtime you want to affect.</span></span> <span data-ttu-id="1a708-113">Para obter o ponto de entrada, chame o [iclrruntimeinfo:: GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) método e especificar "CoEEShutDownCOM".</span><span class="sxs-lookup"><span data-stu-id="1a708-113">To get the entry point, call the [ICLRRuntimeInfo::GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) method and specify "CoEEShutDownCOM".</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a708-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1a708-114">Requirements</span></span>  
 <span data-ttu-id="1a708-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a708-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a708-116">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1a708-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1a708-117">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="1a708-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1a708-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a708-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a708-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1a708-119">See also</span></span>
- [<span data-ttu-id="1a708-120">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="1a708-120">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
