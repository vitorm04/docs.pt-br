---
title: Enumeração COR_PRF_SNAPSHOT_INFO
ms.date: 03/30/2017
api_name:
- COR_PRF_SNAPSHOT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SNAPSHOT_INFO
helpviewer_keywords:
- COR_PRF_SNAPSHOT_INFO enumeration [.NET Framework profiling]
ms.assetid: a5906b2a-ad4a-4cc6-a421-2d7d8adf7468
topic_type:
- apiref
ms.openlocfilehash: 6ade4f7877e39a8307a36f3a3268f79e8b4d44fd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427277"
---
# <a name="cor_prf_snapshot_info-enumeration"></a><span data-ttu-id="c0107-102">Enumeração COR_PRF_SNAPSHOT_INFO</span><span class="sxs-lookup"><span data-stu-id="c0107-102">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>
<span data-ttu-id="c0107-103">Especifica a quantidade de dados a serem passados com um instantâneo de pilha em cada chamada para a função [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) do criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="c0107-103">Specifies how much data to pass back with a stack snapshot in each call to the profiler's [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0107-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c0107-104">Syntax</span></span>  
  
```cpp  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="c0107-105">Membros</span><span class="sxs-lookup"><span data-stu-id="c0107-105">Members</span></span>  
  
|<span data-ttu-id="c0107-106">Membros</span><span class="sxs-lookup"><span data-stu-id="c0107-106">Members</span></span>|<span data-ttu-id="c0107-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0107-107">Description</span></span>|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|<span data-ttu-id="c0107-108">Indica que os valores devem ser passados para todos os parâmetros de `StackSnapshotCallback`, exceto o parâmetro `context`.</span><span class="sxs-lookup"><span data-stu-id="c0107-108">Indicates that values must be passed for all `StackSnapshotCallback` parameters, except the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|<span data-ttu-id="c0107-109">Indica que os valores devem ser passados para todos os parâmetros de `StackSnapshotCallback`, incluindo o parâmetro `context`.</span><span class="sxs-lookup"><span data-stu-id="c0107-109">Indicates that values must be passed for all `StackSnapshotCallback` parameters, including the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|<span data-ttu-id="c0107-110">Indica que um algoritmo de movimentação de pilha mais simples e alternativo será usado.</span><span class="sxs-lookup"><span data-stu-id="c0107-110">Indicates that a simpler, alternative stack-walking algorithm will be used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0107-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="c0107-111">Remarks</span></span>  
 <span data-ttu-id="c0107-112">Os valores fornecidos pela enumeração de `COR_PRF_SNAPSHOT_INFO` são passados como parâmetros para o método [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c0107-112">Values that are provided by the `COR_PRF_SNAPSHOT_INFO` enumeration are passed as parameters to the [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0107-113">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="c0107-113">Requirements</span></span>  
 <span data-ttu-id="c0107-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0107-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0107-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c0107-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c0107-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0107-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0107-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0107-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0107-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c0107-118">See also</span></span>

- [<span data-ttu-id="c0107-119">Método DoStackSnapshot</span><span class="sxs-lookup"><span data-stu-id="c0107-119">DoStackSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="c0107-120">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="c0107-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
