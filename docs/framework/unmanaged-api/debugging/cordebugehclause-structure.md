---
title: Estrutura CorDebugEHClause
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugEHClause
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 0e350a1b-6997-46d0-bfc5-962a5011ef43
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 839e698c8921f916fad174bae4f4cc8bb4d02994
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157320"
---
# <a name="cordebugehclause-structure"></a><span data-ttu-id="71aa7-102">Estrutura CorDebugEHClause</span><span class="sxs-lookup"><span data-stu-id="71aa7-102">CorDebugEHClause Structure</span></span>
<span data-ttu-id="71aa7-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="71aa7-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="71aa7-104">Representa uma cláusula de manipulação de exceção (EH) para um determinado código de linguagem intermediária (IL).</span><span class="sxs-lookup"><span data-stu-id="71aa7-104">Represents an exception handling (EH) clause for a given piece of intermediate language (IL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71aa7-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="71aa7-105">Syntax</span></span>  
  
```cpp
typedef struct _CorDebugEHClause {  
   ULONG32 Flags;  
   ULONG32 TryOffset;  
   ULONG32 TryLength;  
   ULONG32 HandlerOffset;  
   ULONG32 HandlerLength;  
   ULONG32 ClassToken;  
   ULONG32 FilterOffset;  
} CorDebugEHClause;  
```  
  
## <a name="members"></a><span data-ttu-id="71aa7-106">Membros</span><span class="sxs-lookup"><span data-stu-id="71aa7-106">Members</span></span>  
  
|<span data-ttu-id="71aa7-107">Membro</span><span class="sxs-lookup"><span data-stu-id="71aa7-107">Member</span></span>|<span data-ttu-id="71aa7-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="71aa7-108">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="71aa7-109">Um campo de bits que descreve as informações de exceção na cláusula EH.</span><span class="sxs-lookup"><span data-stu-id="71aa7-109">A bit field that describes the exception information in the EH clause.</span></span> <span data-ttu-id="71aa7-110">Para obter mais informações, consulte a seção Comentários.</span><span class="sxs-lookup"><span data-stu-id="71aa7-110">For more information, see the Remarks section.</span></span>|  
|`TryOffset`|<span data-ttu-id="71aa7-111">O deslocamento, em bytes, do bloco `try` a partir do início do corpo do método.</span><span class="sxs-lookup"><span data-stu-id="71aa7-111">The offset, in bytes, of the `try` block from the start of the method body.</span></span>|  
|`TryLength`|<span data-ttu-id="71aa7-112">O tamanho, em bytes, do bloco `try`.</span><span class="sxs-lookup"><span data-stu-id="71aa7-112">The length, in bytes, of the `try` block.</span></span>|  
|`HandlerOffset`|<span data-ttu-id="71aa7-113">A localização do manipulador desse bloco `try`.</span><span class="sxs-lookup"><span data-stu-id="71aa7-113">The location of the handler for this `try` block.</span></span>|  
|`HandlerLength`|<span data-ttu-id="71aa7-114">O tamanho, em bytes, do código do manipulador.</span><span class="sxs-lookup"><span data-stu-id="71aa7-114">The size of the handler code in bytes.</span></span>|  
|`ClassToken`|<span data-ttu-id="71aa7-115">O token de metadados para um manipulador de exceção com base em tipo.</span><span class="sxs-lookup"><span data-stu-id="71aa7-115">The metadata token for a type-based exception handler.</span></span>|  
|`FilterOffset`|<span data-ttu-id="71aa7-116">O deslocamento, em bytes, do início do corpo do método para um manipulador de exceção com base em filtro.</span><span class="sxs-lookup"><span data-stu-id="71aa7-116">The offset, in bytes, from the start of the method body for a filter-based exception handler.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71aa7-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="71aa7-117">Remarks</span></span>  
 <span data-ttu-id="71aa7-118">Uma matriz de `CoreDebugEHClause` valores é retornado pelo [GetEHClauses](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="71aa7-118">An array of `CoreDebugEHClause` values is returned by the [GetEHClauses](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md) method.</span></span>  
  
 <span data-ttu-id="71aa7-119">As informações da cláusula EH são definidas pela especificação CLI.</span><span class="sxs-lookup"><span data-stu-id="71aa7-119">The EH clause information is defined by the CLI specification.</span></span> <span data-ttu-id="71aa7-120">Para obter mais informações, consulte [Standard ECMA-355: Common Language Infrastructure (CLI), 6th Edition](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="71aa7-120">For more information, see [Standard ECMA-355: Common Language Infrastructure (CLI), 6th Edition](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
 <span data-ttu-id="71aa7-121">O campo `flags` pode conter os seguintes sinalizadores.</span><span class="sxs-lookup"><span data-stu-id="71aa7-121">The `flags` field can contain the following flags.</span></span> <span data-ttu-id="71aa7-122">Observe se eles não estão definidos em CorDebug.idl ou em CorDebug.h.</span><span class="sxs-lookup"><span data-stu-id="71aa7-122">Note that they are not defined in CorDebug.idl or CorDebug.h.</span></span>  
  
|<span data-ttu-id="71aa7-123">Sinalizador</span><span class="sxs-lookup"><span data-stu-id="71aa7-123">Flag</span></span>|<span data-ttu-id="71aa7-124">Valor</span><span class="sxs-lookup"><span data-stu-id="71aa7-124">Value</span></span>|<span data-ttu-id="71aa7-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="71aa7-125">Description</span></span>|  
|----------|-----------|-----------------|  
|`COR_ILEXCEPTION_CLAUSE_EXCEPTION`|<span data-ttu-id="71aa7-126">0x00000000</span><span class="sxs-lookup"><span data-stu-id="71aa7-126">0x00000000</span></span>|<span data-ttu-id="71aa7-127">Uma cláusula de exceção digitada.</span><span class="sxs-lookup"><span data-stu-id="71aa7-127">A typed exception clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FILTER`|<span data-ttu-id="71aa7-128">0x00000001</span><span class="sxs-lookup"><span data-stu-id="71aa7-128">0x00000001</span></span>|<span data-ttu-id="71aa7-129">Uma cláusula do manipulador e do filtro de exceção.</span><span class="sxs-lookup"><span data-stu-id="71aa7-129">An exception filter and handler clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FINALLY`|<span data-ttu-id="71aa7-130">0x00000002</span><span class="sxs-lookup"><span data-stu-id="71aa7-130">0x00000002</span></span>|<span data-ttu-id="71aa7-131">Uma cláusula `finally`.</span><span class="sxs-lookup"><span data-stu-id="71aa7-131">A `finally` clause.</span></span>|  
|`COR_ILEXCEPTION_CLAUSE_FAULT`|<span data-ttu-id="71aa7-132">0x00000004</span><span class="sxs-lookup"><span data-stu-id="71aa7-132">0x00000004</span></span>|<span data-ttu-id="71aa7-133">Uma cláusula de falha (uma cláusula `finally` que é chamada somente quando uma exceção é lançada).</span><span class="sxs-lookup"><span data-stu-id="71aa7-133">A fault clause (a `finally` clause that is called only when an exception is thrown).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="71aa7-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="71aa7-134">Requirements</span></span>  
 <span data-ttu-id="71aa7-135">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71aa7-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71aa7-136">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="71aa7-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="71aa7-137">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71aa7-137">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="71aa7-138">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="71aa7-138">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="71aa7-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71aa7-139">See also</span></span>

- [<span data-ttu-id="71aa7-140">Método GetEHClauses</span><span class="sxs-lookup"><span data-stu-id="71aa7-140">GetEHClauses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-getehclauses-method.md)
- [<span data-ttu-id="71aa7-141">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="71aa7-141">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
