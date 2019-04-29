---
title: Estrutura CodeChunkInfo
ms.date: 03/30/2017
api_name:
- CodeChunkInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CodeChunkInfo
helpviewer_keywords:
- CodeChunkInfo structure [.NET Framework debugging]
ms.assetid: 0f482454-8517-48de-ba7a-d7aedab13bb5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58c9d4c66af0bb9f4e66d17b18ac78ef8271bc31
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609601"
---
# <a name="codechunkinfo-structure"></a><span data-ttu-id="8c6c4-102">Estrutura CodeChunkInfo</span><span class="sxs-lookup"><span data-stu-id="8c6c4-102">CodeChunkInfo Structure</span></span>

<span data-ttu-id="8c6c4-103">Representa uma única parte de código na memória.</span><span class="sxs-lookup"><span data-stu-id="8c6c4-103">Represents a single chunk of code in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c6c4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8c6c4-104">Syntax</span></span>  
  
```  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="8c6c4-105">Membros</span><span class="sxs-lookup"><span data-stu-id="8c6c4-105">Members</span></span>  
  
|<span data-ttu-id="8c6c4-106">Membro</span><span class="sxs-lookup"><span data-stu-id="8c6c4-106">Member</span></span>|<span data-ttu-id="8c6c4-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="8c6c4-107">Description</span></span>|  
|------------|-----------------|  
|`startAddr`|<span data-ttu-id="8c6c4-108">Um `CORDB_ADDRESS` valor que especifica o endereço inicial da parte.</span><span class="sxs-lookup"><span data-stu-id="8c6c4-108">A `CORDB_ADDRESS` value that specifies the starting address of the chunk.</span></span>|  
|`length`|<span data-ttu-id="8c6c4-109">O tamanho, em bytes, da parte.</span><span class="sxs-lookup"><span data-stu-id="8c6c4-109">The size, in bytes, of the chunk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c6c4-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="8c6c4-110">Remarks</span></span>  
 <span data-ttu-id="8c6c4-111">A única parte do código é uma região de código nativo que é parte de um objeto de código, como uma função.</span><span class="sxs-lookup"><span data-stu-id="8c6c4-111">The single chunk of code is a region of native code that is part of a code object such as a function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c6c4-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8c6c4-112">Requirements</span></span>  
 <span data-ttu-id="8c6c4-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c6c4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c6c4-114">**Cabeçalho:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="8c6c4-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="8c6c4-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c6c4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c6c4-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c6c4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c6c4-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8c6c4-117">See also</span></span>

- [<span data-ttu-id="8c6c4-118">Método GetCodeChunks</span><span class="sxs-lookup"><span data-stu-id="8c6c4-118">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)
- [<span data-ttu-id="8c6c4-119">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="8c6c4-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="8c6c4-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="8c6c4-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
