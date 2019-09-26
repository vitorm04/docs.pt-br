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
ms.openlocfilehash: 4528ccd77fed2ea2a9b2d08243ffa1535bfad1ae
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274083"
---
# <a name="clr_debugging_version-structure"></a><span data-ttu-id="8a271-102">Estrutura CLR_DEBUGGING_VERSION</span><span class="sxs-lookup"><span data-stu-id="8a271-102">CLR_DEBUGGING_VERSION Structure</span></span>
<span data-ttu-id="8a271-103">Define a versão do produto do CLR (Common Language Runtime) para fins de depuração.</span><span class="sxs-lookup"><span data-stu-id="8a271-103">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a271-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8a271-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="8a271-105">Membros</span><span class="sxs-lookup"><span data-stu-id="8a271-105">Members</span></span>  
  
|<span data-ttu-id="8a271-106">Membro</span><span class="sxs-lookup"><span data-stu-id="8a271-106">Member</span></span>|<span data-ttu-id="8a271-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a271-107">Description</span></span>|  
|------------|-----------------|  
|`wStructVersion`|<span data-ttu-id="8a271-108">O número de versão da estrutura</span><span class="sxs-lookup"><span data-stu-id="8a271-108">The structure version number</span></span>|  
|`wMajor`|<span data-ttu-id="8a271-109">O número da versão principal.</span><span class="sxs-lookup"><span data-stu-id="8a271-109">The major version number.</span></span>|  
|`wMinor`|<span data-ttu-id="8a271-110">O número da versão secundária.</span><span class="sxs-lookup"><span data-stu-id="8a271-110">The minor version number.</span></span>|  
|`wBuild`|<span data-ttu-id="8a271-111">O número de build.</span><span class="sxs-lookup"><span data-stu-id="8a271-111">The build number.</span></span>|  
|`wRevision`|<span data-ttu-id="8a271-112">O número de revisão.</span><span class="sxs-lookup"><span data-stu-id="8a271-112">The revision number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a271-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="8a271-113">Remarks</span></span>  
 <span data-ttu-id="8a271-114">A `CLR_DEBUGGING_VERSION` estrutura é igual à estrutura COR_VERSION, no entanto, a `CLR_DEBUGGING_VERSION` estrutura fornece um campo de versão de estrutura`wStructVersion`adicional ().</span><span class="sxs-lookup"><span data-stu-id="8a271-114">The `CLR_DEBUGGING_VERSION` structure is the same as the COR_VERSION structure, however, the `CLR_DEBUGGING_VERSION` structure provides an additional structure version field (`wStructVersion`).</span></span> <span data-ttu-id="8a271-115">No momento, esse campo deve ser definido como zero.</span><span class="sxs-lookup"><span data-stu-id="8a271-115">Currently, this field must be set to zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a271-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8a271-116">Requirements</span></span>  
 <span data-ttu-id="8a271-117">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a271-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a271-118">**Cabeçalho:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="8a271-118">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="8a271-119">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a271-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a271-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a271-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a271-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a271-121">See also</span></span>

- [<span data-ttu-id="8a271-122">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="8a271-122">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="8a271-123">Depuração</span><span class="sxs-lookup"><span data-stu-id="8a271-123">Debugging</span></span>](index.md)
