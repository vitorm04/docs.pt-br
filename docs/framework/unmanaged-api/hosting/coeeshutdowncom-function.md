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
ms.openlocfilehash: 3eb8bffee9d30a89c39a900e600ebf171456b9f3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616782"
---
# <a name="coeeshutdowncom-function"></a><span data-ttu-id="abee0-102">Função CoEEShutDownCOM</span><span class="sxs-lookup"><span data-stu-id="abee0-102">CoEEShutDownCOM Function</span></span>
<span data-ttu-id="abee0-103">Força o Common Language Runtime (CLR) a liberar todos os ponteiros de interface que ele mantém dentro de RCW (Runtime Callable Wrappers).</span><span class="sxs-lookup"><span data-stu-id="abee0-103">Forces the common language runtime (CLR) to release all interface pointers it holds inside runtime callable wrappers (RCW).</span></span> <span data-ttu-id="abee0-104">Isso tem o efeito de liberar todos os caches de RCW.</span><span class="sxs-lookup"><span data-stu-id="abee0-104">This has the effect of releasing all RCW caches.</span></span> <span data-ttu-id="abee0-105">Essa função global foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="abee0-105">This global function is deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="abee0-106">Em vez disso, use o ponto de entrada para um tempo de execução específico.</span><span class="sxs-lookup"><span data-stu-id="abee0-106">Instead, use the entry point for a specific runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abee0-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="abee0-107">Syntax</span></span>  
  
```cpp  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="abee0-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="abee0-108">Remarks</span></span>  
 <span data-ttu-id="abee0-109">A `CoEEShutDownCOM` função primeiro libera todos os RCWs em todos os contextos e em todos os caches e, em seguida, remove qualquer notificação de subdivisão existente na instalação.</span><span class="sxs-lookup"><span data-stu-id="abee0-109">The `CoEEShutDownCOM` function first releases all the RCWs in all contexts and in all caches, and then removes any tear-down notification existing in setup.</span></span> <span data-ttu-id="abee0-110">Nenhum descarregamento de DLL ocorre.</span><span class="sxs-lookup"><span data-stu-id="abee0-110">No DLL unloading occurs.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="abee0-111">Essa função afeta todos os tempos de execução que são carregados no processo.</span><span class="sxs-lookup"><span data-stu-id="abee0-111">This function affects all runtimes that are loaded into the process.</span></span>  
  
 <span data-ttu-id="abee0-112">Começando com o .NET Framework 4, chame o ponto de entrada para essa função no tempo de execução específico que você deseja afetar.</span><span class="sxs-lookup"><span data-stu-id="abee0-112">Beginning with the .NET Framework 4, call the entry point for this function on the specific runtime you want to affect.</span></span> <span data-ttu-id="abee0-113">Para obter o ponto de entrada, chame o método [ICLRRuntimeInfo:: GetProcAddress](iclrruntimeinfo-getprocaddress-method.md) e especifique "CoEEShutDownCOM".</span><span class="sxs-lookup"><span data-stu-id="abee0-113">To get the entry point, call the [ICLRRuntimeInfo::GetProcAddress](iclrruntimeinfo-getprocaddress-method.md) method and specify "CoEEShutDownCOM".</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abee0-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="abee0-114">Requirements</span></span>  
 <span data-ttu-id="abee0-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abee0-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abee0-116">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="abee0-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="abee0-117">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="abee0-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="abee0-118">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abee0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abee0-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="abee0-119">See also</span></span>

- [<span data-ttu-id="abee0-120">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="abee0-120">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
