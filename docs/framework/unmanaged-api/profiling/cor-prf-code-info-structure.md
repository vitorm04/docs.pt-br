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
ms.openlocfilehash: 56734a9971759b78a835917c4914cf55edaa47a4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59103279"
---
# <a name="corprfcodeinfo-structure"></a><span data-ttu-id="6afb2-102">Estrutura COR_PRF_CODE_INFO</span><span class="sxs-lookup"><span data-stu-id="6afb2-102">COR_PRF_CODE_INFO Structure</span></span>
<span data-ttu-id="6afb2-103">Representa um bloco contíguo de código nativo armazenado na memória.</span><span class="sxs-lookup"><span data-stu-id="6afb2-103">Represents one contiguous block of native code stored in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6afb2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6afb2-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_CODE_INFO {  
    UINT_PTR startAddress;  
    SIZE_T size;  
} COR_PRF_CODE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="6afb2-105">Membros</span><span class="sxs-lookup"><span data-stu-id="6afb2-105">Members</span></span>  
  
|<span data-ttu-id="6afb2-106">Membro</span><span class="sxs-lookup"><span data-stu-id="6afb2-106">Member</span></span>|<span data-ttu-id="6afb2-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="6afb2-107">Description</span></span>|  
|------------|-----------------|  
|`startAddress`|<span data-ttu-id="6afb2-108">O endereço inicial do bloco contíguo de código.</span><span class="sxs-lookup"><span data-stu-id="6afb2-108">The starting address of the contiguous block of code.</span></span>|  
|`size`|<span data-ttu-id="6afb2-109">O tamanho do bloco.</span><span class="sxs-lookup"><span data-stu-id="6afb2-109">The size of the block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6afb2-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6afb2-110">Requirements</span></span>  
 <span data-ttu-id="6afb2-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6afb2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6afb2-112">**Cabeçalho:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="6afb2-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="6afb2-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6afb2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6afb2-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6afb2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6afb2-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6afb2-115">See also</span></span>

- [<span data-ttu-id="6afb2-116">Estruturas de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="6afb2-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
