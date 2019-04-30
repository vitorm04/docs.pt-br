---
title: Estrutura StackTrace_SimpleContext
ms.date: 03/30/2017
api_name:
- StackTrace_SimpleContext
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SimpleContext
helpviewer_keywords:
- SimpleContext structure [.NET Framework debugging]
- StackTrace_SimpleContext structure [.NET Framework debugging]
ms.assetid: d4cef11f-a8ca-49bc-a1b8-6631f9e28f3e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0625dc72d44485dbb69b42cba5387085d1862bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986525"
---
# <a name="stacktracesimplecontext-structure"></a><span data-ttu-id="7f83c-102">Estrutura StackTrace_SimpleContext</span><span class="sxs-lookup"><span data-stu-id="7f83c-102">StackTrace_SimpleContext Structure</span></span>
<span data-ttu-id="7f83c-103">Fornece um contexto simples que pode ser usado em lugar de uma estrutura `CONTEXT` completa.</span><span class="sxs-lookup"><span data-stu-id="7f83c-103">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f83c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7f83c-104">Syntax</span></span>  
  
```  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a><span data-ttu-id="7f83c-105">Membros</span><span class="sxs-lookup"><span data-stu-id="7f83c-105">Members</span></span>  
  
|<span data-ttu-id="7f83c-106">Membro</span><span class="sxs-lookup"><span data-stu-id="7f83c-106">Member</span></span>|<span data-ttu-id="7f83c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="7f83c-107">Description</span></span>|  
|------------|-----------------|  
|`StackOffset`|<span data-ttu-id="7f83c-108">O ponteiro de pilha, ou o ponteiro de pilha de enter (ESP) em x86 plataformas.</span><span class="sxs-lookup"><span data-stu-id="7f83c-108">The stack pointer, or the enter stack pointer (ESP) on x86 platforms.</span></span>|  
|`FrameOffset`|<span data-ttu-id="7f83c-109">O deslocamento do quadro, ou o registro de EBP no x86 plataformas.</span><span class="sxs-lookup"><span data-stu-id="7f83c-109">The frame offset, or the EBP register on x86 platforms.</span></span>|  
|`InstructionOffset`|<span data-ttu-id="7f83c-110">O ponteiro de instrução ou o ponteiro de instrução de enter (EIP) em x86 plataformas.</span><span class="sxs-lookup"><span data-stu-id="7f83c-110">The instruction pointer, or the enter instruction pointer (EIP) on x86 platforms.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f83c-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="7f83c-111">Remarks</span></span>  
 <span data-ttu-id="7f83c-112">Como as funções de rastreamento de pilha normalmente precisam retornar apenas o endereço, deslocamento do quadro e endereço de pilha, opcionalmente, você pode usar o `SimpleContext` estrutura em vez de um grande `CONTEXT` estrutura.</span><span class="sxs-lookup"><span data-stu-id="7f83c-112">Because stack trace functions typically need to return only the address, frame offset, and stack address, you can optionally use the `SimpleContext` structure instead of a large `CONTEXT` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f83c-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7f83c-113">Requirements</span></span>  
 <span data-ttu-id="7f83c-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f83c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f83c-115">**Cabeçalho:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="7f83c-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="7f83c-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f83c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f83c-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7f83c-117">See also</span></span>

- [<span data-ttu-id="7f83c-118">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="7f83c-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="7f83c-119">Depuração</span><span class="sxs-lookup"><span data-stu-id="7f83c-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
