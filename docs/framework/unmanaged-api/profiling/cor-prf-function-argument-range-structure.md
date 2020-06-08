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
ms.openlocfilehash: 8b3785955ec138bbf898e84aa4deb5ed2a6e6b53
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500943"
---
# <a name="cor_prf_function_argument_range-structure"></a><span data-ttu-id="ed5eb-102">Estrutura COR_PRF_FUNCTION_ARGUMENT_RANGE</span><span class="sxs-lookup"><span data-stu-id="ed5eb-102">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>
<span data-ttu-id="ed5eb-103">Representa um bloco de argumentos de função armazenados de forma contígua em ordem da esquerda para a direita na memória.</span><span class="sxs-lookup"><span data-stu-id="ed5eb-103">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed5eb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ed5eb-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_RANGE {  
    UINT_PTR startAddress;  
    ULONG length;  
} COR_PRF_FUNCTION_ARGUMENT_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="ed5eb-105">Membros</span><span class="sxs-lookup"><span data-stu-id="ed5eb-105">Members</span></span>  
  
|<span data-ttu-id="ed5eb-106">Membros</span><span class="sxs-lookup"><span data-stu-id="ed5eb-106">Members</span></span>|<span data-ttu-id="ed5eb-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="ed5eb-107">Description</span></span>|  
|-------------|-----------------|  
|`startAddress`|<span data-ttu-id="ed5eb-108">O endereço inicial do bloco.</span><span class="sxs-lookup"><span data-stu-id="ed5eb-108">The starting address of the block.</span></span>|  
|`length`|<span data-ttu-id="ed5eb-109">O comprimento do bloco contíguo.</span><span class="sxs-lookup"><span data-stu-id="ed5eb-109">The length of the contiguous block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ed5eb-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ed5eb-110">Requirements</span></span>  
 <span data-ttu-id="ed5eb-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed5eb-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed5eb-112">**Cabeçalho:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="ed5eb-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="ed5eb-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ed5eb-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed5eb-114">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed5eb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed5eb-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="ed5eb-115">See also</span></span>

- [<span data-ttu-id="ed5eb-116">Estruturas de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="ed5eb-116">Profiling Structures</span></span>](profiling-structures.md)
