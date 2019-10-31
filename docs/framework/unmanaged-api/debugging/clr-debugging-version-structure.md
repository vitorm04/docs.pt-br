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
ms.openlocfilehash: 651b916a0e3ca178432094428611f9bcc8f0fd17
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132425"
---
# <a name="clr_debugging_version-structure"></a><span data-ttu-id="b03d1-102">Estrutura CLR_DEBUGGING_VERSION</span><span class="sxs-lookup"><span data-stu-id="b03d1-102">CLR_DEBUGGING_VERSION Structure</span></span>
<span data-ttu-id="b03d1-103">Define a versão do produto do CLR (Common Language Runtime) para fins de depuração.</span><span class="sxs-lookup"><span data-stu-id="b03d1-103">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b03d1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b03d1-104">Syntax</span></span>  
  
```cpp  
typedef struct _CLR_DEBUGGING_VERSION  
{  
    WORD wStructVersion;
    WORD wMajor;
    WORD wMinor;
    WORD wBuild;
    WORD wRevision;
} CLR_DEBUGGING_VERSION;
```  
  
## <a name="members"></a><span data-ttu-id="b03d1-105">Membros</span><span class="sxs-lookup"><span data-stu-id="b03d1-105">Members</span></span>  
  
|<span data-ttu-id="b03d1-106">Membro</span><span class="sxs-lookup"><span data-stu-id="b03d1-106">Member</span></span>|<span data-ttu-id="b03d1-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b03d1-107">Description</span></span>|  
|------------|-----------------|  
|`wStructVersion`|<span data-ttu-id="b03d1-108">O número de versão da estrutura</span><span class="sxs-lookup"><span data-stu-id="b03d1-108">The structure version number</span></span>|  
|`wMajor`|<span data-ttu-id="b03d1-109">O número da versão principal.</span><span class="sxs-lookup"><span data-stu-id="b03d1-109">The major version number.</span></span>|  
|`wMinor`|<span data-ttu-id="b03d1-110">O número da versão secundária.</span><span class="sxs-lookup"><span data-stu-id="b03d1-110">The minor version number.</span></span>|  
|`wBuild`|<span data-ttu-id="b03d1-111">O número de build.</span><span class="sxs-lookup"><span data-stu-id="b03d1-111">The build number.</span></span>|  
|`wRevision`|<span data-ttu-id="b03d1-112">O número de revisão.</span><span class="sxs-lookup"><span data-stu-id="b03d1-112">The revision number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b03d1-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="b03d1-113">Remarks</span></span>  
 <span data-ttu-id="b03d1-114">A estrutura de `CLR_DEBUGGING_VERSION` é igual à estrutura COR_VERSION, no entanto, a estrutura de `CLR_DEBUGGING_VERSION` fornece um campo de versão de estrutura adicional (`wStructVersion`).</span><span class="sxs-lookup"><span data-stu-id="b03d1-114">The `CLR_DEBUGGING_VERSION` structure is the same as the COR_VERSION structure, however, the `CLR_DEBUGGING_VERSION` structure provides an additional structure version field (`wStructVersion`).</span></span> <span data-ttu-id="b03d1-115">No momento, esse campo deve ser definido como zero.</span><span class="sxs-lookup"><span data-stu-id="b03d1-115">Currently, this field must be set to zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b03d1-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b03d1-116">Requirements</span></span>  
 <span data-ttu-id="b03d1-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b03d1-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b03d1-118">**Cabeçalho:** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="b03d1-118">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="b03d1-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b03d1-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b03d1-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b03d1-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b03d1-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b03d1-121">See also</span></span>

- [<span data-ttu-id="b03d1-122">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="b03d1-122">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="b03d1-123">Depuração</span><span class="sxs-lookup"><span data-stu-id="b03d1-123">Debugging</span></span>](index.md)
