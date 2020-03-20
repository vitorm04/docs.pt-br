---
title: Estrutura COR_HEAPINFO
ms.date: 03/30/2017
api_name:
- COR_HEAPINFO
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPINFO
helpviewer_keywords:
- COR_HEAPINFO structure [.NET Framework debugging]
ms.assetid: bfb2cd39-3e0b-4d51-ba0c-f009755c1456
topic_type:
- apiref
ms.openlocfilehash: 37659262695b63a6dd6390c62c4bb7e04fdadca4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179302"
---
# <a name="cor_heapinfo-structure"></a><span data-ttu-id="da8b1-102">Estrutura COR_HEAPINFO</span><span class="sxs-lookup"><span data-stu-id="da8b1-102">COR_HEAPINFO Structure</span></span>
<span data-ttu-id="da8b1-103">Fornece informações gerais sobre o heap de coleta de lixo, incluindo se é enumerável.</span><span class="sxs-lookup"><span data-stu-id="da8b1-103">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da8b1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="da8b1-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;
    DWORD pointerSize;
    DWORD numHeaps;  
    BOOL concurrent;
    CorDebugGCType gcType;
} COR_HEAPINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="da8b1-105">Membros</span><span class="sxs-lookup"><span data-stu-id="da8b1-105">Members</span></span>  
  
|<span data-ttu-id="da8b1-106">Membro</span><span class="sxs-lookup"><span data-stu-id="da8b1-106">Member</span></span>|<span data-ttu-id="da8b1-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="da8b1-107">Description</span></span>|  
|------------|-----------------|  
|`areGCStructuresValid`|<span data-ttu-id="da8b1-108">`true`se as estruturas de coleta de lixo forem válidas e o monte puder ser enumerado; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="da8b1-108">`true` if garbage collection structures are valid and the heap can be enumerated; otherwise, `false`.</span></span>|  
|`pointerSize`|<span data-ttu-id="da8b1-109">O tamanho, em bytes, de ponteiros na arquitetura alvo.</span><span class="sxs-lookup"><span data-stu-id="da8b1-109">The size, in bytes, of pointers on the target architecture.</span></span>|  
|`numHeaps`|<span data-ttu-id="da8b1-110">O número de montes lógicos de coleta de lixo no processo.</span><span class="sxs-lookup"><span data-stu-id="da8b1-110">The number of logical garbage collection heaps in the process.</span></span>|  
|`concurrent`|<span data-ttu-id="da8b1-111">`TRUE`se a coleta de lixo simultânea (fundo) estiver habilitada; caso contrário, `FALSE`.</span><span class="sxs-lookup"><span data-stu-id="da8b1-111">`TRUE` if concurrent (background) garbage collection is enabled; otherwise, `FALSE`.</span></span>|  
|`gcType`|<span data-ttu-id="da8b1-112">Um membro da [enumeração CorDebugGCType](cordebuggctype-enumeration.md) que indica se o coletor de lixo está sendo executado em uma estação de trabalho ou em um servidor.</span><span class="sxs-lookup"><span data-stu-id="da8b1-112">A member of the [CorDebugGCType](cordebuggctype-enumeration.md) enumeration that indicates whether the garbage collector is running on a workstation or a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da8b1-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="da8b1-113">Remarks</span></span>  
 <span data-ttu-id="da8b1-114">Uma instância `COR_HEAPINFO` da estrutura é devolvida chamando o método [ICorDebugProcess5::GetGCHeapInformation.](icordebugprocess5-getgcheapinformation-method.md)</span><span class="sxs-lookup"><span data-stu-id="da8b1-114">An instance of the `COR_HEAPINFO` structure is returned by calling the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
 <span data-ttu-id="da8b1-115">Antes de enumerar objetos no monte de `areGCStructuresValid` coleta de lixo, você deve sempre verificar o campo para garantir que o monte esteja em um estado enumerado.</span><span class="sxs-lookup"><span data-stu-id="da8b1-115">Before enumerating objects on the garbage collection heap, you must always check the `areGCStructuresValid` field to ensure that the heap is in an enumerable state.</span></span> <span data-ttu-id="da8b1-116">Para obter mais informações, consulte o método [ICorDebugProcess5::GetGCHeapInformation.](icordebugprocess5-getgcheapinformation-method.md)</span><span class="sxs-lookup"><span data-stu-id="da8b1-116">For more information, see the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da8b1-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="da8b1-117">Requirements</span></span>  
 <span data-ttu-id="da8b1-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da8b1-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da8b1-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="da8b1-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da8b1-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da8b1-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da8b1-121">**.NET Framework Versions:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da8b1-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da8b1-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="da8b1-122">See also</span></span>

- [<span data-ttu-id="da8b1-123">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="da8b1-123">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="da8b1-124">Depuração</span><span class="sxs-lookup"><span data-stu-id="da8b1-124">Debugging</span></span>](index.md)
