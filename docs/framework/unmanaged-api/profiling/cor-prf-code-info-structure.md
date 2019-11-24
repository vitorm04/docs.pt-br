---
title: Estrutura COR_PRF_CODE_INFO
ms.date: 03/30/2017
api_name:
- COR_PRF_CODE_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CODE_INFO
helpviewer_keywords:
- COR_PRF_CODE_INFO structure [.NET Framework profiling]
ms.assetid: cf30e27c-1f7e-43a2-ba1e-01e4137301db
topic_type:
- apiref
ms.openlocfilehash: 643c9d7104c374d9141a604083f3fdcd540156c4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428393"
---
# <a name="cor_prf_code_info-structure"></a><span data-ttu-id="76ad9-102">Estrutura COR_PRF_CODE_INFO</span><span class="sxs-lookup"><span data-stu-id="76ad9-102">COR_PRF_CODE_INFO Structure</span></span>
<span data-ttu-id="76ad9-103">Representa um bloco contíguo de código nativo armazenado na memória.</span><span class="sxs-lookup"><span data-stu-id="76ad9-103">Represents one contiguous block of native code stored in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76ad9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="76ad9-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_CODE_INFO {  
    UINT_PTR startAddress;  
    SIZE_T size;  
} COR_PRF_CODE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="76ad9-105">Membros</span><span class="sxs-lookup"><span data-stu-id="76ad9-105">Members</span></span>  
  
|<span data-ttu-id="76ad9-106">Membro</span><span class="sxs-lookup"><span data-stu-id="76ad9-106">Member</span></span>|<span data-ttu-id="76ad9-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="76ad9-107">Description</span></span>|  
|------------|-----------------|  
|`startAddress`|<span data-ttu-id="76ad9-108">The starting address of the contiguous block of code.</span><span class="sxs-lookup"><span data-stu-id="76ad9-108">The starting address of the contiguous block of code.</span></span>|  
|`size`|<span data-ttu-id="76ad9-109">The size of the block.</span><span class="sxs-lookup"><span data-stu-id="76ad9-109">The size of the block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="76ad9-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="76ad9-110">Requirements</span></span>  
 <span data-ttu-id="76ad9-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76ad9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76ad9-112">**Header:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="76ad9-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="76ad9-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76ad9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76ad9-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76ad9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76ad9-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="76ad9-115">See also</span></span>

- [<span data-ttu-id="76ad9-116">Estruturas de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="76ad9-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
