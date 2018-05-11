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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 852e6cbd666441b92afb583b15b72d50d26eff8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="corprfcodeinfo-structure"></a><span data-ttu-id="e3cb7-102">Estrutura COR_PRF_CODE_INFO</span><span class="sxs-lookup"><span data-stu-id="e3cb7-102">COR_PRF_CODE_INFO Structure</span></span>
<span data-ttu-id="e3cb7-103">Representa um bloco contíguo de código nativo armazenado na memória.</span><span class="sxs-lookup"><span data-stu-id="e3cb7-103">Represents one contiguous block of native code stored in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3cb7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e3cb7-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_CODE_INFO {  
    UINT_PTR startAddress;  
    SIZE_T size;  
} COR_PRF_CODE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="e3cb7-105">Membros</span><span class="sxs-lookup"><span data-stu-id="e3cb7-105">Members</span></span>  
  
|<span data-ttu-id="e3cb7-106">Membro</span><span class="sxs-lookup"><span data-stu-id="e3cb7-106">Member</span></span>|<span data-ttu-id="e3cb7-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e3cb7-107">Description</span></span>|  
|------------|-----------------|  
|`startAddress`|<span data-ttu-id="e3cb7-108">O endereço inicial do bloco de contígua de código.</span><span class="sxs-lookup"><span data-stu-id="e3cb7-108">The starting address of the contiguous block of code.</span></span>|  
|`size`|<span data-ttu-id="e3cb7-109">O tamanho do bloco.</span><span class="sxs-lookup"><span data-stu-id="e3cb7-109">The size of the block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e3cb7-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e3cb7-110">Requirements</span></span>  
 <span data-ttu-id="e3cb7-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3cb7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3cb7-112">**Cabeçalho:** Corprof. idl</span><span class="sxs-lookup"><span data-stu-id="e3cb7-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="e3cb7-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3cb7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3cb7-114">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3cb7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3cb7-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e3cb7-115">See Also</span></span>  
 [<span data-ttu-id="e3cb7-116">Estruturas de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="e3cb7-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
