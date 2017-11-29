---
title: Estrutura COR_VERSION
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_VERSION
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_VERSION
helpviewer_keywords: COR_VERSION structure [.NET Framework debugging]
ms.assetid: 5efaee1c-a001-4c73-9525-4160f4c71567
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bd4a878b51685befb39eb486097be2e2f2c1d409
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="corversion-structure"></a><span data-ttu-id="7a74a-102">Estrutura COR_VERSION</span><span class="sxs-lookup"><span data-stu-id="7a74a-102">COR_VERSION Structure</span></span>
<span data-ttu-id="7a74a-103">Armazena o número da versão com quatro partes padrão do CLR.</span><span class="sxs-lookup"><span data-stu-id="7a74a-103">Stores the standard four-part version number of the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a74a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7a74a-104">Syntax</span></span>  
  
```  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="7a74a-105">Membros</span><span class="sxs-lookup"><span data-stu-id="7a74a-105">Members</span></span>  
  
|<span data-ttu-id="7a74a-106">Membro</span><span class="sxs-lookup"><span data-stu-id="7a74a-106">Member</span></span>|<span data-ttu-id="7a74a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="7a74a-107">Description</span></span>|  
|------------|-----------------|  
|`dwMajor`|<span data-ttu-id="7a74a-108">O número da versão principal.</span><span class="sxs-lookup"><span data-stu-id="7a74a-108">The major version number.</span></span>|  
|`dwMinor`|<span data-ttu-id="7a74a-109">O número da versão secundária.</span><span class="sxs-lookup"><span data-stu-id="7a74a-109">The minor version number.</span></span>|  
|`dwBuild`|<span data-ttu-id="7a74a-110">O número de compilação.</span><span class="sxs-lookup"><span data-stu-id="7a74a-110">The build number.</span></span>|  
|`dwSubBuild`|<span data-ttu-id="7a74a-111">O número de compilação sub.</span><span class="sxs-lookup"><span data-stu-id="7a74a-111">The sub-build number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a74a-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="7a74a-112">Remarks</span></span>  
 <span data-ttu-id="7a74a-113">Se o número de versão é 1.0.3705.288, 1 é o número de versão principal, 0 é o número de versão secundária, 3705 é o número de compilação e 288 é o número de compilação sub.</span><span class="sxs-lookup"><span data-stu-id="7a74a-113">If the version number is 1.0.3705.288, 1 is the major version number, 0 is the minor version number, 3705 is the build number, and 288 is the sub-build number.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a74a-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7a74a-114">Requirements</span></span>  
 <span data-ttu-id="7a74a-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a74a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a74a-116">**Cabeçalho:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="7a74a-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="7a74a-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a74a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a74a-118">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a74a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a74a-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7a74a-119">See Also</span></span>  
 [<span data-ttu-id="7a74a-120">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="7a74a-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="7a74a-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="7a74a-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
