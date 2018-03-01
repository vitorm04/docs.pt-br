---
title: Estrutura COR_VERSION
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- COR_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_VERSION
helpviewer_keywords:
- COR_VERSION structure [.NET Framework debugging]
ms.assetid: 5efaee1c-a001-4c73-9525-4160f4c71567
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b527cb9175315af98a9ad4e9be06d459ad6e188e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="corversion-structure"></a><span data-ttu-id="68889-102">Estrutura COR_VERSION</span><span class="sxs-lookup"><span data-stu-id="68889-102">COR_VERSION Structure</span></span>
<span data-ttu-id="68889-103">Armazena o número da versão com quatro partes padrão do CLR.</span><span class="sxs-lookup"><span data-stu-id="68889-103">Stores the standard four-part version number of the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68889-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="68889-104">Syntax</span></span>  
  
```  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="68889-105">Membros</span><span class="sxs-lookup"><span data-stu-id="68889-105">Members</span></span>  
  
|<span data-ttu-id="68889-106">Membro</span><span class="sxs-lookup"><span data-stu-id="68889-106">Member</span></span>|<span data-ttu-id="68889-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="68889-107">Description</span></span>|  
|------------|-----------------|  
|`dwMajor`|<span data-ttu-id="68889-108">O número da versão principal.</span><span class="sxs-lookup"><span data-stu-id="68889-108">The major version number.</span></span>|  
|`dwMinor`|<span data-ttu-id="68889-109">O número da versão secundária.</span><span class="sxs-lookup"><span data-stu-id="68889-109">The minor version number.</span></span>|  
|`dwBuild`|<span data-ttu-id="68889-110">O número de build.</span><span class="sxs-lookup"><span data-stu-id="68889-110">The build number.</span></span>|  
|`dwSubBuild`|<span data-ttu-id="68889-111">O número de compilação sub.</span><span class="sxs-lookup"><span data-stu-id="68889-111">The sub-build number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68889-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="68889-112">Remarks</span></span>  
 <span data-ttu-id="68889-113">Se o número de versão é 1.0.3705.288, 1 é o número de versão principal, 0 é o número de versão secundária, 3705 é o número de compilação e 288 é o número de compilação sub.</span><span class="sxs-lookup"><span data-stu-id="68889-113">If the version number is 1.0.3705.288, 1 is the major version number, 0 is the minor version number, 3705 is the build number, and 288 is the sub-build number.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68889-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="68889-114">Requirements</span></span>  
 <span data-ttu-id="68889-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68889-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68889-116">**Cabeçalho:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="68889-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="68889-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68889-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68889-118">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68889-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68889-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="68889-119">See Also</span></span>  
 [<span data-ttu-id="68889-120">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="68889-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="68889-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="68889-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
