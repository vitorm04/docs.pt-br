---
title: Estrutura COR_PRF_FUNCTION_ARGUMENT_RANGE
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7f61d23fc3ee3c6c8adb46c0deecdd72d155ae65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="corprffunctionargumentrange-structure"></a><span data-ttu-id="1958c-102">Estrutura COR_PRF_FUNCTION_ARGUMENT_RANGE</span><span class="sxs-lookup"><span data-stu-id="1958c-102">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>
<span data-ttu-id="1958c-103">Representa um bloco de argumentos de função armazenados de forma contígua em ordem da esquerda para a direita na memória.</span><span class="sxs-lookup"><span data-stu-id="1958c-103">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1958c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1958c-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_RANGE {  
    UINT_PTR startAddress;  
    ULONG length;  
} COR_PRF_FUNCTION_ARGUMENT_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="1958c-105">Membros</span><span class="sxs-lookup"><span data-stu-id="1958c-105">Members</span></span>  
  
|<span data-ttu-id="1958c-106">Membros</span><span class="sxs-lookup"><span data-stu-id="1958c-106">Members</span></span>|<span data-ttu-id="1958c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="1958c-107">Description</span></span>|  
|-------------|-----------------|  
|`startAddress`|<span data-ttu-id="1958c-108">O endereço inicial do bloco.</span><span class="sxs-lookup"><span data-stu-id="1958c-108">The starting address of the block.</span></span>|  
|`length`|<span data-ttu-id="1958c-109">O comprimento do bloco de contígua.</span><span class="sxs-lookup"><span data-stu-id="1958c-109">The length of the contiguous block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1958c-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1958c-110">Requirements</span></span>  
 <span data-ttu-id="1958c-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1958c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1958c-112">**Cabeçalho:** Corprof. idl</span><span class="sxs-lookup"><span data-stu-id="1958c-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="1958c-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1958c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1958c-114">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1958c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1958c-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1958c-115">See Also</span></span>  
 [<span data-ttu-id="1958c-116">Estruturas de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="1958c-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
