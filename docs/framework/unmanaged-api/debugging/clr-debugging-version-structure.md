---
title: Estrutura CLR_DEBUGGING_VERSION
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLR_DEBUGGING_VERSION
api_location: mscordbi.dll
api_type: COM
f1_keywords: CLR_DEBUGGING_VERSION
helpviewer_keywords: CLR_DEBUGGING_VERSION structure [.NET Framework debugging]
ms.assetid: 4d821186-3ddf-405a-ac44-d79438a9f7f3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 98124b7b9efb2c92ebee6b6e99f73edc6cf173a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="clrdebuggingversion-structure"></a><span data-ttu-id="8480e-102">Estrutura CLR_DEBUGGING_VERSION</span><span class="sxs-lookup"><span data-stu-id="8480e-102">CLR_DEBUGGING_VERSION Structure</span></span>
<span data-ttu-id="8480e-103">Define a versão do produto do CLR (Common Language Runtime) para fins de depuração.</span><span class="sxs-lookup"><span data-stu-id="8480e-103">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8480e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8480e-104">Syntax</span></span>  
  
```  
Typedef struct _CLR_DEBUGGING_VERSION  
{  
WORD wStructVersion;  
WORD wMajor;   
WORD wMinor;  
WORD wBuild;  
WORD wRevision;  
}  CLR_DEBUGGING_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="8480e-105">Membros</span><span class="sxs-lookup"><span data-stu-id="8480e-105">Members</span></span>  
  
|<span data-ttu-id="8480e-106">Membro</span><span class="sxs-lookup"><span data-stu-id="8480e-106">Member</span></span>|<span data-ttu-id="8480e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="8480e-107">Description</span></span>|  
|------------|-----------------|  
|`wStructVersion`|<span data-ttu-id="8480e-108">O número de versão de estrutura</span><span class="sxs-lookup"><span data-stu-id="8480e-108">The structure version number</span></span>|  
|`wMajor`|<span data-ttu-id="8480e-109">O número da versão principal.</span><span class="sxs-lookup"><span data-stu-id="8480e-109">The major version number.</span></span>|  
|`wMinor`|<span data-ttu-id="8480e-110">O número da versão secundária.</span><span class="sxs-lookup"><span data-stu-id="8480e-110">The minor version number.</span></span>|  
|`wBuild`|<span data-ttu-id="8480e-111">O número de compilação.</span><span class="sxs-lookup"><span data-stu-id="8480e-111">The build number.</span></span>|  
|`wRevision`|<span data-ttu-id="8480e-112">O número de revisão.</span><span class="sxs-lookup"><span data-stu-id="8480e-112">The revision number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8480e-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="8480e-113">Remarks</span></span>  
 <span data-ttu-id="8480e-114">O `CLR_DEBUGGING_VERSION` estrutura é a mesma que a estrutura COR_VERSION, no entanto, o `CLR_DEBUGGING_VERSION` estrutura fornece um campo de versão de estrutura adicional (`wStructVersion`).</span><span class="sxs-lookup"><span data-stu-id="8480e-114">The `CLR_DEBUGGING_VERSION` structure is the same as the COR_VERSION structure, however, the `CLR_DEBUGGING_VERSION` structure provides an additional structure version field (`wStructVersion`).</span></span> <span data-ttu-id="8480e-115">Atualmente, este campo deve ser definido como zero.</span><span class="sxs-lookup"><span data-stu-id="8480e-115">Currently, this field must be set to zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8480e-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8480e-116">Requirements</span></span>  
 <span data-ttu-id="8480e-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8480e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8480e-118">**Cabeçalho:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="8480e-118">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="8480e-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8480e-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8480e-120">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8480e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8480e-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8480e-121">See Also</span></span>  
 [<span data-ttu-id="8480e-122">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="8480e-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="8480e-123">Depuração</span><span class="sxs-lookup"><span data-stu-id="8480e-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
