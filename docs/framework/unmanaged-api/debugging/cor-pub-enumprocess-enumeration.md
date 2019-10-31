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
ms.openlocfilehash: f789105751ae2d498740ab60f326f9c0597483b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099207"
---
# <a name="cor_pub_enumprocess-enumeration"></a><span data-ttu-id="772bf-102">Enumeração COR_PUB_ENUMPROCESS</span><span class="sxs-lookup"><span data-stu-id="772bf-102">COR_PUB_ENUMPROCESS Enumeration</span></span>
<span data-ttu-id="772bf-103">Identifica o tipo de processo que será enumerado.</span><span class="sxs-lookup"><span data-stu-id="772bf-103">Identifies the type of process to be enumerated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="772bf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="772bf-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PUB_MANAGEDONLY    = 0x00000001  
} COR_PUB_ENUMPROCESS;  
```  
  
## <a name="members"></a><span data-ttu-id="772bf-105">Membros</span><span class="sxs-lookup"><span data-stu-id="772bf-105">Members</span></span>  
  
|<span data-ttu-id="772bf-106">Nome do membro</span><span class="sxs-lookup"><span data-stu-id="772bf-106">Member name</span></span>|<span data-ttu-id="772bf-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="772bf-107">Description</span></span>|  
|-----------------|-----------------|  
|`COR_PUB_MANAGEDONLY`|<span data-ttu-id="772bf-108">Um processo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="772bf-108">A managed process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="772bf-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="772bf-109">Remarks</span></span>  
 <span data-ttu-id="772bf-110">A versão atual da API de depuração não gerenciada enumera somente os processos gerenciados.</span><span class="sxs-lookup"><span data-stu-id="772bf-110">The current version of the unmanaged debugging API enumerates only managed processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="772bf-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="772bf-111">Requirements</span></span>  
 <span data-ttu-id="772bf-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="772bf-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="772bf-113">**Cabeçalho:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="772bf-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="772bf-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="772bf-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="772bf-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="772bf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="772bf-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="772bf-116">See also</span></span>

- [<span data-ttu-id="772bf-117">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="772bf-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
