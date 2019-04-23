---
title: Estrutura CLR_DEBUGGING_VERSION
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_VERSION
helpviewer_keywords:
- CLR_DEBUGGING_VERSION structure [.NET Framework debugging]
ms.assetid: 4d821186-3ddf-405a-ac44-d79438a9f7f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 87f938a7119abe4a88da65bd779a5f4a02499516
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59117112"
---
# <a name="clrdebuggingversion-structure"></a><span data-ttu-id="48690-102">Estrutura CLR_DEBUGGING_VERSION</span><span class="sxs-lookup"><span data-stu-id="48690-102">CLR_DEBUGGING_VERSION Structure</span></span>
<span data-ttu-id="48690-103">Define a versão do produto do CLR (Common Language Runtime) para fins de depuração.</span><span class="sxs-lookup"><span data-stu-id="48690-103">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48690-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="48690-104">Syntax</span></span>  
  
```  
typedef struct _CLR_DEBUGGING_VERSION  
{  
    WORD wStructVersion;
    WORD wMajor;
    WORD wMinor;
    WORD wBuild;
    WORD wRevision;
} CLR_DEBUGGING_VERSION;
```  
  
## <a name="members"></a><span data-ttu-id="48690-105">Membros</span><span class="sxs-lookup"><span data-stu-id="48690-105">Members</span></span>  
  
|<span data-ttu-id="48690-106">Membro</span><span class="sxs-lookup"><span data-stu-id="48690-106">Member</span></span>|<span data-ttu-id="48690-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="48690-107">Description</span></span>|  
|------------|-----------------|  
|`wStructVersion`|<span data-ttu-id="48690-108">O número de versão de estrutura</span><span class="sxs-lookup"><span data-stu-id="48690-108">The structure version number</span></span>|  
|`wMajor`|<span data-ttu-id="48690-109">O número da versão principal.</span><span class="sxs-lookup"><span data-stu-id="48690-109">The major version number.</span></span>|  
|`wMinor`|<span data-ttu-id="48690-110">O número da versão secundária.</span><span class="sxs-lookup"><span data-stu-id="48690-110">The minor version number.</span></span>|  
|`wBuild`|<span data-ttu-id="48690-111">O número de build.</span><span class="sxs-lookup"><span data-stu-id="48690-111">The build number.</span></span>|  
|`wRevision`|<span data-ttu-id="48690-112">O número de revisão.</span><span class="sxs-lookup"><span data-stu-id="48690-112">The revision number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48690-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="48690-113">Remarks</span></span>  
 <span data-ttu-id="48690-114">O `CLR_DEBUGGING_VERSION` estrutura é o mesmo que a estrutura COR_VERSION, no entanto, o `CLR_DEBUGGING_VERSION` estrutura fornece um campo de versão de estrutura adicional (`wStructVersion`).</span><span class="sxs-lookup"><span data-stu-id="48690-114">The `CLR_DEBUGGING_VERSION` structure is the same as the COR_VERSION structure, however, the `CLR_DEBUGGING_VERSION` structure provides an additional structure version field (`wStructVersion`).</span></span> <span data-ttu-id="48690-115">Atualmente, esse campo deve ser definido como zero.</span><span class="sxs-lookup"><span data-stu-id="48690-115">Currently, this field must be set to zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48690-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="48690-116">Requirements</span></span>  
 <span data-ttu-id="48690-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48690-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48690-118">**Cabeçalho:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="48690-118">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="48690-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48690-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48690-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48690-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48690-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48690-121">See also</span></span>

- [<span data-ttu-id="48690-122">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="48690-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="48690-123">Depuração</span><span class="sxs-lookup"><span data-stu-id="48690-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
