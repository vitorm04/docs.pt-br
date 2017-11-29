---
title: Estrutura CodeChunkInfo 1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CodeChunkInfo
api_location: mscordbi.dll
api_type: COM
f1_keywords: CodeChunkInfo
helpviewer_keywords: CodeChunkInfo structure [.NET Framework debugging]
ms.assetid: 0f482454-8517-48de-ba7a-d7aedab13bb5
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 17727c8927f9db3de3ab26d2504dfae5215a1495
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="codechunkinfo-structure1"></a><span data-ttu-id="b5f49-102">Estrutura CodeChunkInfo 1</span><span class="sxs-lookup"><span data-stu-id="b5f49-102">CodeChunkInfo Structure1</span></span>
<span data-ttu-id="b5f49-103">Representa uma única parte de código na memória.</span><span class="sxs-lookup"><span data-stu-id="b5f49-103">Represents a single chunk of code in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5f49-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b5f49-104">Syntax</span></span>  
  
```  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="b5f49-105">Membros</span><span class="sxs-lookup"><span data-stu-id="b5f49-105">Members</span></span>  
  
|<span data-ttu-id="b5f49-106">Membro</span><span class="sxs-lookup"><span data-stu-id="b5f49-106">Member</span></span>|<span data-ttu-id="b5f49-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b5f49-107">Description</span></span>|  
|------------|-----------------|  
|`startAddr`|<span data-ttu-id="b5f49-108">Um `CORDB_ADDRESS` valor que especifica o endereço inicial da parte.</span><span class="sxs-lookup"><span data-stu-id="b5f49-108">A `CORDB_ADDRESS` value that specifies the starting address of the chunk.</span></span>|  
|`length`|<span data-ttu-id="b5f49-109">O tamanho, em bytes, da parte.</span><span class="sxs-lookup"><span data-stu-id="b5f49-109">The size, in bytes, of the chunk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5f49-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="b5f49-110">Remarks</span></span>  
 <span data-ttu-id="b5f49-111">A única parte do código é uma região de código nativo que é parte de um objeto de código, como uma função.</span><span class="sxs-lookup"><span data-stu-id="b5f49-111">The single chunk of code is a region of native code that is part of a code object such as a function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5f49-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b5f49-112">Requirements</span></span>  
 <span data-ttu-id="b5f49-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5f49-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5f49-114">**Cabeçalho:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="b5f49-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="b5f49-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5f49-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5f49-116">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5f49-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5f49-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5f49-117">See Also</span></span>  
 [<span data-ttu-id="b5f49-118">Método GetCodeChunks</span><span class="sxs-lookup"><span data-stu-id="b5f49-118">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)  
 [<span data-ttu-id="b5f49-119">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="b5f49-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="b5f49-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="b5f49-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
