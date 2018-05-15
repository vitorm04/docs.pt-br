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
ms.openlocfilehash: 1bc8d588641163ccf98054fdf1930a72a04c770c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="corprffunction-structure"></a><span data-ttu-id="30f37-102">Estrutura COR_PRF_FUNCTION</span><span class="sxs-lookup"><span data-stu-id="30f37-102">COR_PRF_FUNCTION Structure</span></span>
<span data-ttu-id="30f37-103">Fornece uma representação única de uma função pela combinação de sua ID com a ID de sua versão recompilada.</span><span class="sxs-lookup"><span data-stu-id="30f37-103">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30f37-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="30f37-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION {    FunctionID functionId;    ReJITID    reJitId;} COR_PRF_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="30f37-105">Membros</span><span class="sxs-lookup"><span data-stu-id="30f37-105">Members</span></span>  
  
|<span data-ttu-id="30f37-106">Membro</span><span class="sxs-lookup"><span data-stu-id="30f37-106">Member</span></span>|<span data-ttu-id="30f37-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="30f37-107">Description</span></span>|  
|------------|-----------------|  
|`functionId`|<span data-ttu-id="30f37-108">A ID da função.</span><span class="sxs-lookup"><span data-stu-id="30f37-108">The ID of the function.</span></span>|  
|`reJitId`|<span data-ttu-id="30f37-109">A ID da função recompilada.</span><span class="sxs-lookup"><span data-stu-id="30f37-109">The ID of the recompiled function.</span></span> <span data-ttu-id="30f37-110">Um valor de 0 (zero) representa a versão original da função.</span><span class="sxs-lookup"><span data-stu-id="30f37-110">A value of 0 (zero) represents the original version of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30f37-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="30f37-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30f37-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="30f37-112">Requirements</span></span>  
 <span data-ttu-id="30f37-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30f37-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30f37-114">**Cabeçalho:** Corprof. idl</span><span class="sxs-lookup"><span data-stu-id="30f37-114">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="30f37-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30f37-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30f37-116">**Versões do .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30f37-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30f37-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30f37-117">See Also</span></span>  
 [<span data-ttu-id="30f37-118">Estruturas de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="30f37-118">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
