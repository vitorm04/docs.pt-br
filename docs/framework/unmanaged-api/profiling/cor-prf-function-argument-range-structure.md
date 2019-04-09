---
title: Estrutura COR_PRF_FUNCTION_ARGUMENT_RANGE
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION_ARGUMENT_RANGE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION_ARGUMENT_RANGE
helpviewer_keywords:
- COR_PRF_FUNCTION_ARGUMENT_RANGE structure [.NET Framework profiling'
ms.assetid: 9f469eac-ac66-419b-8668-fe705bc1a51f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dffefedf14d5f219736e429be191021b2de7ddd2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125587"
---
# <a name="corprffunctionargumentrange-structure"></a><span data-ttu-id="7757f-102">Estrutura COR_PRF_FUNCTION_ARGUMENT_RANGE</span><span class="sxs-lookup"><span data-stu-id="7757f-102">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>
<span data-ttu-id="7757f-103">Representa um bloco de argumentos de função armazenados de forma contígua em ordem da esquerda para a direita na memória.</span><span class="sxs-lookup"><span data-stu-id="7757f-103">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7757f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7757f-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_RANGE {  
    UINT_PTR startAddress;  
    ULONG length;  
} COR_PRF_FUNCTION_ARGUMENT_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="7757f-105">Membros</span><span class="sxs-lookup"><span data-stu-id="7757f-105">Members</span></span>  
  
|<span data-ttu-id="7757f-106">Membros</span><span class="sxs-lookup"><span data-stu-id="7757f-106">Members</span></span>|<span data-ttu-id="7757f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="7757f-107">Description</span></span>|  
|-------------|-----------------|  
|`startAddress`|<span data-ttu-id="7757f-108">O endereço inicial do bloco.</span><span class="sxs-lookup"><span data-stu-id="7757f-108">The starting address of the block.</span></span>|  
|`length`|<span data-ttu-id="7757f-109">O tamanho do bloco contíguo.</span><span class="sxs-lookup"><span data-stu-id="7757f-109">The length of the contiguous block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7757f-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7757f-110">Requirements</span></span>  
 <span data-ttu-id="7757f-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7757f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7757f-112">**Cabeçalho:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="7757f-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="7757f-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7757f-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="7757f-114">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="7757f-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7757f-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7757f-115">See also</span></span>

- [<span data-ttu-id="7757f-116">Estruturas de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="7757f-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
