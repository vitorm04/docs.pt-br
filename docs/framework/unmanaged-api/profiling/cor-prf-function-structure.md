---
title: Estrutura COR_PRF_FUNCTION
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION
helpviewer_keywords:
- COR_PRF_FUNCTION structure [.NET Framework profiling]
ms.assetid: 8bb5acf5-cf4b-4ccb-93f1-46db1f3f8bf3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 14d42a4032c3e2b1c231414678912e1658e759d4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59101719"
---
# <a name="corprffunction-structure"></a><span data-ttu-id="1fba5-102">Estrutura COR_PRF_FUNCTION</span><span class="sxs-lookup"><span data-stu-id="1fba5-102">COR_PRF_FUNCTION Structure</span></span>
<span data-ttu-id="1fba5-103">Fornece uma representação única de uma função pela combinação de sua ID com a ID de sua versão recompilada.</span><span class="sxs-lookup"><span data-stu-id="1fba5-103">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fba5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1fba5-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION {    FunctionID functionId;    ReJITID    reJitId;} COR_PRF_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="1fba5-105">Membros</span><span class="sxs-lookup"><span data-stu-id="1fba5-105">Members</span></span>  
  
|<span data-ttu-id="1fba5-106">Membro</span><span class="sxs-lookup"><span data-stu-id="1fba5-106">Member</span></span>|<span data-ttu-id="1fba5-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="1fba5-107">Description</span></span>|  
|------------|-----------------|  
|`functionId`|<span data-ttu-id="1fba5-108">A ID da função.</span><span class="sxs-lookup"><span data-stu-id="1fba5-108">The ID of the function.</span></span>|  
|`reJitId`|<span data-ttu-id="1fba5-109">A ID da função recompilada.</span><span class="sxs-lookup"><span data-stu-id="1fba5-109">The ID of the recompiled function.</span></span> <span data-ttu-id="1fba5-110">Um valor de 0 (zero) representa a versão original da função.</span><span class="sxs-lookup"><span data-stu-id="1fba5-110">A value of 0 (zero) represents the original version of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1fba5-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="1fba5-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fba5-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1fba5-112">Requirements</span></span>  
 <span data-ttu-id="1fba5-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1fba5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fba5-114">**Cabeçalho:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="1fba5-114">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="1fba5-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1fba5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1fba5-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fba5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fba5-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1fba5-117">See also</span></span>

- [<span data-ttu-id="1fba5-118">Estruturas de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="1fba5-118">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
