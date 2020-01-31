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
ms.openlocfilehash: eaab5b7faeac3dd0fb64f0a387f437af44e7bc12
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867302"
---
# <a name="cor_prf_code_info-structure"></a><span data-ttu-id="007bc-102">Estrutura COR_PRF_CODE_INFO</span><span class="sxs-lookup"><span data-stu-id="007bc-102">COR_PRF_CODE_INFO Structure</span></span>
<span data-ttu-id="007bc-103">Representa um bloco contíguo de código nativo armazenado na memória.</span><span class="sxs-lookup"><span data-stu-id="007bc-103">Represents one contiguous block of native code stored in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="007bc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="007bc-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_CODE_INFO {  
    UINT_PTR startAddress;  
    SIZE_T size;  
} COR_PRF_CODE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="007bc-105">Membros</span><span class="sxs-lookup"><span data-stu-id="007bc-105">Members</span></span>  
  
|<span data-ttu-id="007bc-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="007bc-106">Member</span></span>|<span data-ttu-id="007bc-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="007bc-107">Description</span></span>|  
|------------|-----------------|  
|`startAddress`|<span data-ttu-id="007bc-108">O endereço inicial do bloco de código contíguo.</span><span class="sxs-lookup"><span data-stu-id="007bc-108">The starting address of the contiguous block of code.</span></span>|  
|`size`|<span data-ttu-id="007bc-109">O tamanho do bloco.</span><span class="sxs-lookup"><span data-stu-id="007bc-109">The size of the block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="007bc-110">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="007bc-110">Requirements</span></span>  
 <span data-ttu-id="007bc-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="007bc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="007bc-112">**Cabeçalho:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="007bc-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="007bc-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="007bc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="007bc-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="007bc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="007bc-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="007bc-115">See also</span></span>

- [<span data-ttu-id="007bc-116">Estruturas de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="007bc-116">Profiling Structures</span></span>](profiling-structures.md)
