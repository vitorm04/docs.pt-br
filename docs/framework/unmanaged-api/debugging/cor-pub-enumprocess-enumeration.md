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
ms.openlocfilehash: 412e2bb7da7b5b3396342df169d56d2724ddb466
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740556"
---
# <a name="corpubenumprocess-enumeration"></a><span data-ttu-id="2021c-102">Enumeração COR_PUB_ENUMPROCESS</span><span class="sxs-lookup"><span data-stu-id="2021c-102">COR_PUB_ENUMPROCESS Enumeration</span></span>
<span data-ttu-id="2021c-103">Identifica o tipo de processo que será enumerado.</span><span class="sxs-lookup"><span data-stu-id="2021c-103">Identifies the type of process to be enumerated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2021c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2021c-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PUB_MANAGEDONLY    = 0x00000001  
} COR_PUB_ENUMPROCESS;  
```  
  
## <a name="members"></a><span data-ttu-id="2021c-105">Membros</span><span class="sxs-lookup"><span data-stu-id="2021c-105">Members</span></span>  
  
|<span data-ttu-id="2021c-106">Nome do membro</span><span class="sxs-lookup"><span data-stu-id="2021c-106">Member name</span></span>|<span data-ttu-id="2021c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2021c-107">Description</span></span>|  
|-----------------|-----------------|  
|`COR_PUB_MANAGEDONLY`|<span data-ttu-id="2021c-108">Um processo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="2021c-108">A managed process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2021c-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="2021c-109">Remarks</span></span>  
 <span data-ttu-id="2021c-110">A versão atual da API de depuração não gerenciada enumera somente os processos gerenciados.</span><span class="sxs-lookup"><span data-stu-id="2021c-110">The current version of the unmanaged debugging API enumerates only managed processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2021c-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2021c-111">Requirements</span></span>  
 <span data-ttu-id="2021c-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2021c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2021c-113">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="2021c-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="2021c-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2021c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2021c-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2021c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2021c-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2021c-116">See also</span></span>

- [<span data-ttu-id="2021c-117">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="2021c-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
