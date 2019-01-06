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
ms.openlocfilehash: fecd5af43f4b984a4ab626e9832b3318715c0516
ms.sourcegitcommit: deb9225a55485a5a6e6c7914deb30ccfceb69d3f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/05/2019
ms.locfileid: "54058354"
---
# <a name="clrdebuggingversion-structure"></a><span data-ttu-id="1caae-102">Estrutura CLR_DEBUGGING_VERSION</span><span class="sxs-lookup"><span data-stu-id="1caae-102">CLR_DEBUGGING_VERSION Structure</span></span>
<span data-ttu-id="1caae-103">Define a versão do produto do CLR (Common Language Runtime) para fins de depuração.</span><span class="sxs-lookup"><span data-stu-id="1caae-103">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1caae-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1caae-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="1caae-105">Membros</span><span class="sxs-lookup"><span data-stu-id="1caae-105">Members</span></span>  
  
|<span data-ttu-id="1caae-106">Membro</span><span class="sxs-lookup"><span data-stu-id="1caae-106">Member</span></span>|<span data-ttu-id="1caae-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="1caae-107">Description</span></span>|  
|------------|-----------------|  
|`wStructVersion`|<span data-ttu-id="1caae-108">O número de versão de estrutura</span><span class="sxs-lookup"><span data-stu-id="1caae-108">The structure version number</span></span>|  
|`wMajor`|<span data-ttu-id="1caae-109">O número da versão principal.</span><span class="sxs-lookup"><span data-stu-id="1caae-109">The major version number.</span></span>|  
|`wMinor`|<span data-ttu-id="1caae-110">O número da versão secundária.</span><span class="sxs-lookup"><span data-stu-id="1caae-110">The minor version number.</span></span>|  
|`wBuild`|<span data-ttu-id="1caae-111">O número de build.</span><span class="sxs-lookup"><span data-stu-id="1caae-111">The build number.</span></span>|  
|`wRevision`|<span data-ttu-id="1caae-112">O número de revisão.</span><span class="sxs-lookup"><span data-stu-id="1caae-112">The revision number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1caae-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="1caae-113">Remarks</span></span>  
 <span data-ttu-id="1caae-114">O `CLR_DEBUGGING_VERSION` estrutura é o mesmo que a estrutura COR_VERSION, no entanto, o `CLR_DEBUGGING_VERSION` estrutura fornece um campo de versão de estrutura adicional (`wStructVersion`).</span><span class="sxs-lookup"><span data-stu-id="1caae-114">The `CLR_DEBUGGING_VERSION` structure is the same as the COR_VERSION structure, however, the `CLR_DEBUGGING_VERSION` structure provides an additional structure version field (`wStructVersion`).</span></span> <span data-ttu-id="1caae-115">Atualmente, esse campo deve ser definido como zero.</span><span class="sxs-lookup"><span data-stu-id="1caae-115">Currently, this field must be set to zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1caae-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1caae-116">Requirements</span></span>  
 <span data-ttu-id="1caae-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1caae-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1caae-118">**Cabeçalho:** Cordebug. idl</span><span class="sxs-lookup"><span data-stu-id="1caae-118">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="1caae-119">**Biblioteca:** Corguids. lib</span><span class="sxs-lookup"><span data-stu-id="1caae-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1caae-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1caae-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1caae-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1caae-121">See Also</span></span>  
 [<span data-ttu-id="1caae-122">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="1caae-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="1caae-123">Depuração</span><span class="sxs-lookup"><span data-stu-id="1caae-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
