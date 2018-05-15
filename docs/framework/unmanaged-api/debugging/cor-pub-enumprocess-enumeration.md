---
title: Enumeração COR_PUB_ENUMPROCESS
ms.date: 03/30/2017
api_name:
- COR_PUB_ENUMPROCESS
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_PUB_ENUMPROCESS
helpviewer_keywords:
- COR_PUB_ENUMPROCESS enumeration [.NET Framework debugging]
ms.assetid: 5d3ada6e-feea-47da-a7ed-b664107c137f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fcdb5883e109d7e0c73c8fb76ee61b52cf23091f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="corpubenumprocess-enumeration"></a><span data-ttu-id="a0e37-102">Enumeração COR_PUB_ENUMPROCESS</span><span class="sxs-lookup"><span data-stu-id="a0e37-102">COR_PUB_ENUMPROCESS Enumeration</span></span>
<span data-ttu-id="a0e37-103">Identifica o tipo de processo que será enumerado.</span><span class="sxs-lookup"><span data-stu-id="a0e37-103">Identifies the type of process to be enumerated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0e37-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a0e37-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PUB_MANAGEDONLY    = 0x00000001  
} COR_PUB_ENUMPROCESS;  
```  
  
## <a name="members"></a><span data-ttu-id="a0e37-105">Membros</span><span class="sxs-lookup"><span data-stu-id="a0e37-105">Members</span></span>  
  
|<span data-ttu-id="a0e37-106">Nome do membro</span><span class="sxs-lookup"><span data-stu-id="a0e37-106">Member name</span></span>|<span data-ttu-id="a0e37-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a0e37-107">Description</span></span>|  
|-----------------|-----------------|  
|`COR_PUB_MANAGEDONLY`|<span data-ttu-id="a0e37-108">Um processo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a0e37-108">A managed process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0e37-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="a0e37-109">Remarks</span></span>  
 <span data-ttu-id="a0e37-110">A versão atual da API de depuração não gerenciada enumera somente os processos gerenciados.</span><span class="sxs-lookup"><span data-stu-id="a0e37-110">The current version of the unmanaged debugging API enumerates only managed processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0e37-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a0e37-111">Requirements</span></span>  
 <span data-ttu-id="a0e37-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0e37-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0e37-113">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="a0e37-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="a0e37-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0e37-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0e37-115">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0e37-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0e37-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0e37-116">See Also</span></span>  
 [<span data-ttu-id="a0e37-117">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="a0e37-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
