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
ms.openlocfilehash: 4e85a9a98bf0550fa906f8b905c73890948f4ac1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124934"
---
# <a name="coeeshutdowncom-function"></a><span data-ttu-id="ecc99-102">Função CoEEShutDownCOM</span><span class="sxs-lookup"><span data-stu-id="ecc99-102">CoEEShutDownCOM Function</span></span>
<span data-ttu-id="ecc99-103">Força o Common Language Runtime (CLR) a liberar todos os ponteiros de interface que ele mantém dentro de RCW (Runtime Callable Wrappers).</span><span class="sxs-lookup"><span data-stu-id="ecc99-103">Forces the common language runtime (CLR) to release all interface pointers it holds inside runtime callable wrappers (RCW).</span></span> <span data-ttu-id="ecc99-104">Isso tem o efeito de liberar todos os caches de RCW.</span><span class="sxs-lookup"><span data-stu-id="ecc99-104">This has the effect of releasing all RCW caches.</span></span> <span data-ttu-id="ecc99-105">Essa função global foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="ecc99-105">This global function is deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="ecc99-106">Em vez disso, use o ponto de entrada para um tempo de execução específico.</span><span class="sxs-lookup"><span data-stu-id="ecc99-106">Instead, use the entry point for a specific runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecc99-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ecc99-107">Syntax</span></span>  
  
```cpp  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="ecc99-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="ecc99-108">Remarks</span></span>  
 <span data-ttu-id="ecc99-109">A função `CoEEShutDownCOM` primeiro libera todos os RCWs em todos os contextos e em todos os caches e, em seguida, remove qualquer notificação de subdivisão existente na instalação.</span><span class="sxs-lookup"><span data-stu-id="ecc99-109">The `CoEEShutDownCOM` function first releases all the RCWs in all contexts and in all caches, and then removes any tear-down notification existing in setup.</span></span> <span data-ttu-id="ecc99-110">Nenhum descarregamento de DLL ocorre.</span><span class="sxs-lookup"><span data-stu-id="ecc99-110">No DLL unloading occurs.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="ecc99-111">Essa função afeta todos os tempos de execução que são carregados no processo.</span><span class="sxs-lookup"><span data-stu-id="ecc99-111">This function affects all runtimes that are loaded into the process.</span></span>  
  
 <span data-ttu-id="ecc99-112">Começando com o .NET Framework 4, chame o ponto de entrada para essa função no tempo de execução específico que você deseja afetar.</span><span class="sxs-lookup"><span data-stu-id="ecc99-112">Beginning with the .NET Framework 4, call the entry point for this function on the specific runtime you want to affect.</span></span> <span data-ttu-id="ecc99-113">Para obter o ponto de entrada, chame o método [ICLRRuntimeInfo:: GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) e especifique "CoEEShutDownCOM".</span><span class="sxs-lookup"><span data-stu-id="ecc99-113">To get the entry point, call the [ICLRRuntimeInfo::GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) method and specify "CoEEShutDownCOM".</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecc99-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ecc99-114">Requirements</span></span>  
 <span data-ttu-id="ecc99-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecc99-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecc99-116">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ecc99-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ecc99-117">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ecc99-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ecc99-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecc99-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecc99-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ecc99-119">See also</span></span>

- [<span data-ttu-id="ecc99-120">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="ecc99-120">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
