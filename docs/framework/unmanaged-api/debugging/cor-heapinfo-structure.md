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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7b340a73aa9eaebca9c0d78563ae298557039b8
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274185"
---
# <a name="cor_heapinfo-structure"></a><span data-ttu-id="c784a-102">Estrutura COR_HEAPINFO</span><span class="sxs-lookup"><span data-stu-id="c784a-102">COR_HEAPINFO Structure</span></span>
<span data-ttu-id="c784a-103">Fornece informações gerais sobre o heap de coleta de lixo, incluindo se é enumerável.</span><span class="sxs-lookup"><span data-stu-id="c784a-103">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c784a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c784a-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;   
    DWORD pointerSize;   
    DWORD numHeaps;  
    BOOL concurrent;   
    CorDebugGCType gcType;   
} COR_HEAPINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="c784a-105">Membros</span><span class="sxs-lookup"><span data-stu-id="c784a-105">Members</span></span>  
  
|<span data-ttu-id="c784a-106">Membro</span><span class="sxs-lookup"><span data-stu-id="c784a-106">Member</span></span>|<span data-ttu-id="c784a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c784a-107">Description</span></span>|  
|------------|-----------------|  
|`areGCStructuresValid`|<span data-ttu-id="c784a-108">`true`Se as estruturas de coleta de lixo forem válidas e o heap puder ser enumerado; caso contrário `false`,.</span><span class="sxs-lookup"><span data-stu-id="c784a-108">`true` if garbage collection structures are valid and the heap can be enumerated; otherwise, `false`.</span></span>|  
|`pointerSize`|<span data-ttu-id="c784a-109">O tamanho, em bytes, dos ponteiros na arquitetura de destino.</span><span class="sxs-lookup"><span data-stu-id="c784a-109">The size, in bytes, of pointers on the target architecture.</span></span>|  
|`numHeaps`|<span data-ttu-id="c784a-110">O número de heaps de coleta de lixo lógico no processo.</span><span class="sxs-lookup"><span data-stu-id="c784a-110">The number of logical garbage collection heaps in the process.</span></span>|  
|`concurrent`|<span data-ttu-id="c784a-111">`TRUE`se a coleta de lixo (em segundo plano) simultânea estiver habilitada; caso contrário `FALSE`,.</span><span class="sxs-lookup"><span data-stu-id="c784a-111">`TRUE` if concurrent (background) garbage collection is enabled; otherwise, `FALSE`.</span></span>|  
|`gcType`|<span data-ttu-id="c784a-112">Um membro da enumeração [CorDebugGCType](cordebuggctype-enumeration.md) que indica se o coletor de lixo está em execução em uma estação de trabalho ou em um servidor.</span><span class="sxs-lookup"><span data-stu-id="c784a-112">A member of the [CorDebugGCType](cordebuggctype-enumeration.md) enumeration that indicates whether the garbage collector is running on a workstation or a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c784a-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="c784a-113">Remarks</span></span>  
 <span data-ttu-id="c784a-114">Uma instância da `COR_HEAPINFO` estrutura é retornada chamando o método [ICorDebugProcess5:: GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c784a-114">An instance of the `COR_HEAPINFO` structure is returned by calling the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
 <span data-ttu-id="c784a-115">Antes de enumerar objetos no heap de coleta de lixo, você sempre deve `areGCStructuresValid` verificar o campo para garantir que o heap esteja em um estado enumerável.</span><span class="sxs-lookup"><span data-stu-id="c784a-115">Before enumerating objects on the garbage collection heap, you must always check the `areGCStructuresValid` field to ensure that the heap is in an enumerable state.</span></span> <span data-ttu-id="c784a-116">Para obter mais informações, consulte o método [ICorDebugProcess5:: GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c784a-116">For more information, see the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c784a-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c784a-117">Requirements</span></span>  
 <span data-ttu-id="c784a-118">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c784a-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c784a-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c784a-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c784a-120">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c784a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c784a-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c784a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c784a-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c784a-122">See also</span></span>

- [<span data-ttu-id="c784a-123">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="c784a-123">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="c784a-124">Depuração</span><span class="sxs-lookup"><span data-stu-id="c784a-124">Debugging</span></span>](index.md)
