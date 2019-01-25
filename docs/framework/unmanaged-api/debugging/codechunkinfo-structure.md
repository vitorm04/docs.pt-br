---
title: Estrutura1 CodeChunkInfo
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
ms.openlocfilehash: d658e360fcfd3fda837c6d7ccab9458594ce9641
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522538"
---
# <a name="codechunkinfo-structure1"></a><span data-ttu-id="708ad-102">Estrutura1 CodeChunkInfo</span><span class="sxs-lookup"><span data-stu-id="708ad-102">CodeChunkInfo Structure1</span></span>
<span data-ttu-id="708ad-103">Representa uma única parte de código na memória.</span><span class="sxs-lookup"><span data-stu-id="708ad-103">Represents a single chunk of code in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="708ad-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="708ad-104">Syntax</span></span>  
  
```  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="708ad-105">Membros</span><span class="sxs-lookup"><span data-stu-id="708ad-105">Members</span></span>  
  
|<span data-ttu-id="708ad-106">Membro</span><span class="sxs-lookup"><span data-stu-id="708ad-106">Member</span></span>|<span data-ttu-id="708ad-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="708ad-107">Description</span></span>|  
|------------|-----------------|  
|`startAddr`|<span data-ttu-id="708ad-108">Um `CORDB_ADDRESS` valor que especifica o endereço inicial da parte.</span><span class="sxs-lookup"><span data-stu-id="708ad-108">A `CORDB_ADDRESS` value that specifies the starting address of the chunk.</span></span>|  
|`length`|<span data-ttu-id="708ad-109">O tamanho, em bytes, da parte.</span><span class="sxs-lookup"><span data-stu-id="708ad-109">The size, in bytes, of the chunk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="708ad-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="708ad-110">Remarks</span></span>  
 <span data-ttu-id="708ad-111">A única parte do código é uma região de código nativo que é parte de um objeto de código, como uma função.</span><span class="sxs-lookup"><span data-stu-id="708ad-111">The single chunk of code is a region of native code that is part of a code object such as a function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="708ad-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="708ad-112">Requirements</span></span>  
 <span data-ttu-id="708ad-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="708ad-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="708ad-114">**Cabeçalho:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="708ad-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="708ad-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="708ad-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="708ad-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="708ad-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="708ad-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="708ad-117">See also</span></span>
- [<span data-ttu-id="708ad-118">Método GetCodeChunks</span><span class="sxs-lookup"><span data-stu-id="708ad-118">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)
- [<span data-ttu-id="708ad-119">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="708ad-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="708ad-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="708ad-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
