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
# <a name="cor_prf_code_info-structure"></a><span data-ttu-id="331cc-102">Estrutura COR_PRF_CODE_INFO</span><span class="sxs-lookup"><span data-stu-id="331cc-102">COR_PRF_CODE_INFO Structure</span></span>
<span data-ttu-id="331cc-103">Representa um bloco contíguo de código nativo armazenado na memória.</span><span class="sxs-lookup"><span data-stu-id="331cc-103">Represents one contiguous block of native code stored in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="331cc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="331cc-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_CODE_INFO {  
    UINT_PTR startAddress;  
    SIZE_T size;  
} COR_PRF_CODE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="331cc-105">Membros</span><span class="sxs-lookup"><span data-stu-id="331cc-105">Members</span></span>  
  
|<span data-ttu-id="331cc-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="331cc-106">Member</span></span>|<span data-ttu-id="331cc-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="331cc-107">Description</span></span>|  
|------------|-----------------|  
|`startAddress`|<span data-ttu-id="331cc-108">O endereço inicial do bloco de código contíguo.</span><span class="sxs-lookup"><span data-stu-id="331cc-108">The starting address of the contiguous block of code.</span></span>|  
|`size`|<span data-ttu-id="331cc-109">O tamanho do bloco.</span><span class="sxs-lookup"><span data-stu-id="331cc-109">The size of the block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="331cc-110">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="331cc-110">Requirements</span></span>  
 <span data-ttu-id="331cc-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="331cc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="331cc-112">**Cabeçalho:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="331cc-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="331cc-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="331cc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="331cc-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="331cc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="331cc-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="331cc-115">See also</span></span>

- [<span data-ttu-id="331cc-116">Estruturas de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="331cc-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
