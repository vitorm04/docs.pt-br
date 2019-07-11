---
title: Enumeração CorDebugRegister
ms.date: 03/30/2017
api_name:
- CorDebugRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugRegister
helpviewer_keywords:
- CorDebugRegister enumeration [.NET Framework debugging]
ms.assetid: 003bb138-7960-4291-ac88-0d87e470ff70
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bed3c461935c5a2bc912ed9ed16d147fddaf8a1a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739657"
---
# <a name="cordebugregister-enumeration"></a><span data-ttu-id="9f12d-102">Enumeração CorDebugRegister</span><span class="sxs-lookup"><span data-stu-id="9f12d-102">CorDebugRegister Enumeration</span></span>
<span data-ttu-id="9f12d-103">Especifica os registros associados a uma determinada arquitetura de processador.</span><span class="sxs-lookup"><span data-stu-id="9f12d-103">Specifies the registers associated with a given processor architecture.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f12d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9f12d-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugRegister {  
  
    REGISTER_INSTRUCTION_POINTER = 0,  
    REGISTER_STACK_POINTER,  
    REGISTER_FRAME_POINTER,  
  
    REGISTER_X86_EIP = 0,  
    REGISTER_X86_ESP,  
    REGISTER_X86_EBP,  
  
    REGISTER_X86_EAX,  
    REGISTER_X86_ECX,  
    REGISTER_X86_EDX,  
    REGISTER_X86_EBX,  
  
    REGISTER_X86_ESI,  
    REGISTER_X86_EDI,  
  
    REGISTER_X86_FPSTACK_0,  
    REGISTER_X86_FPSTACK_1,  
    REGISTER_X86_FPSTACK_2,  
    REGISTER_X86_FPSTACK_3,  
    REGISTER_X86_FPSTACK_4,  
    REGISTER_X86_FPSTACK_5,  
    REGISTER_X86_FPSTACK_6,  
    REGISTER_X86_FPSTACK_7,  
  
    REGISTER_AMD64_RIP = 0,  
    REGISTER_AMD64_RSP,  
    REGISTER_AMD64_RBP,  
    REGISTER_AMD64_RAX,  
    REGISTER_AMD64_RCX,  
    REGISTER_AMD64_RDX,  
    REGISTER_AMD64_RBX,  
    REGISTER_AMD64_RSI,  
    REGISTER_AMD64_RDI,  
    REGISTER_AMD64_R8,  
    REGISTER_AMD64_R9,  
    REGISTER_AMD64_R10,  
    REGISTER_AMD64_R11,  
    REGISTER_AMD64_R12,  
    REGISTER_AMD64_R13,  
    REGISTER_AMD64_R14,  
    REGISTER_AMD64_R15,  
  
    REGISTER_AMD64_XMM0,  
    REGISTER_AMD64_XMM1,  
    REGISTER_AMD64_XMM2,  
    REGISTER_AMD64_XMM3,  
    REGISTER_AMD64_XMM4,  
    REGISTER_AMD64_XMM5,  
    REGISTER_AMD64_XMM6,  
    REGISTER_AMD64_XMM7,  
    REGISTER_AMD64_XMM8,  
    REGISTER_AMD64_XMM9,  
    REGISTER_AMD64_XMM10,  
    REGISTER_AMD64_XMM11,  
    REGISTER_AMD64_XMM12,  
    REGISTER_AMD64_XMM13,  
    REGISTER_AMD64_XMM14,  
    REGISTER_AMD64_XMM15,  
  
    REGISTER_IA64_BSP = REGISTER_FRAME_POINTER,  
    REGISTER_IA64_R0  = REGISTER_IA64_BSP + 1,  
    REGISTER_IA64_F0  = REGISTER_IA64_R0  + 128,  
    REGISTER_ARM_PC = 0,  
    REGISTER_ARM_SP,  
    REGISTER_ARM_R0,  
    REGISTER_ARM_R1,  
    REGISTER_ARM_R2,  
    REGISTER_ARM_R3,  
    REGISTER_ARM_R4,  
    REGISTER_ARM_R5,  
    REGISTER_ARM_R6,  
    REGISTER_ARM_R7,  
    REGISTER_ARM_R8,  
    REGISTER_ARM_R9,  
    REGISTER_ARM_R10,  
    REGISTER_ARM_R11,  
    REGISTER_ARM_R12,  
    REGISTER_ARM_LR,  
  
} CorDebugRegister;  
```  
  
## <a name="members"></a><span data-ttu-id="9f12d-105">Membros</span><span class="sxs-lookup"><span data-stu-id="9f12d-105">Members</span></span>  
  
|<span data-ttu-id="9f12d-106">Membro</span><span class="sxs-lookup"><span data-stu-id="9f12d-106">Member</span></span>|<span data-ttu-id="9f12d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f12d-107">Description</span></span>|  
|------------|-----------------|  
|`REGISTER_INSTRUCTION_POINTER`|<span data-ttu-id="9f12d-108">Um registro de ponteiro de instrução em qualquer processador.</span><span class="sxs-lookup"><span data-stu-id="9f12d-108">An instruction pointer register on any processor.</span></span>|  
|`REGISTER_STACK_POINTER`|<span data-ttu-id="9f12d-109">Um registro de ponteiro de pilha em qualquer processador.</span><span class="sxs-lookup"><span data-stu-id="9f12d-109">A stack pointer register on any processor.</span></span>|  
|`REGISTER_FRAME_POINTER`|<span data-ttu-id="9f12d-110">Um registro de ponteiro de quadro em qualquer processador.</span><span class="sxs-lookup"><span data-stu-id="9f12d-110">A frame pointer register on any processor.</span></span>|  
|`REGISTER_X86_EIP`|<span data-ttu-id="9f12d-111">O registro de ponteiro de instrução no processador x86.</span><span class="sxs-lookup"><span data-stu-id="9f12d-111">The instruction pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_ESP`|<span data-ttu-id="9f12d-112">O registro de ponteiro de pilha no processador x86.</span><span class="sxs-lookup"><span data-stu-id="9f12d-112">The stack pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_EBP`|<span data-ttu-id="9f12d-113">O registro de ponteiro de base no processador x86.</span><span class="sxs-lookup"><span data-stu-id="9f12d-113">The base pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_EAX`|<span data-ttu-id="9f12d-114">O registro de dados A no processador x86.</span><span class="sxs-lookup"><span data-stu-id="9f12d-114">The A data register on the x86 processor.</span></span>|  
|`REGISTER_X86_ECX`|<span data-ttu-id="9f12d-115">O registro de dados C no processador x86.</span><span class="sxs-lookup"><span data-stu-id="9f12d-115">The C data register on the x86 processor.</span></span>|  
|`REGISTER_X86_EDX`|<span data-ttu-id="9f12d-116">O registro de dados D no processador x86.</span><span class="sxs-lookup"><span data-stu-id="9f12d-116">The D data register on the x86 processor.</span></span>|  
|`REGISTER_X86_EBX`|<span data-ttu-id="9f12d-117">O registro de dados B no processador x86.</span><span class="sxs-lookup"><span data-stu-id="9f12d-117">The B data register on the x86 processor.</span></span>|  
|`REGISTER_X86_ESI`|<span data-ttu-id="9f12d-118">O registro de índice de origem no processador x86.</span><span class="sxs-lookup"><span data-stu-id="9f12d-118">The source index register on the x86 processor.</span></span>|  
|`REGISTER_X86_EDI`|<span data-ttu-id="9f12d-119">O registro de índice de destino no processador x86.</span><span class="sxs-lookup"><span data-stu-id="9f12d-119">The destination index register on the x86 processor.</span></span>|  
|`REGISTER_X86_FPSTACK_0`|<span data-ttu-id="9f12d-120">O registro de pilha 0 no processador x86 de ponto flutuante (FP).</span><span class="sxs-lookup"><span data-stu-id="9f12d-120">The stack register 0 on the x86 floating-point (FP) processor.</span></span>|  
|`REGISTER_X86_FPSTACK_1`|<span data-ttu-id="9f12d-121">O registro de pilha #1 no processador x86 de FP.</span><span class="sxs-lookup"><span data-stu-id="9f12d-121">The #1 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_2`|<span data-ttu-id="9f12d-122">O registro de pilha #2 no processador x86 de FP.</span><span class="sxs-lookup"><span data-stu-id="9f12d-122">The #2 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_3`|<span data-ttu-id="9f12d-123">O registro de pilha #3 no processador x86 de FP.</span><span class="sxs-lookup"><span data-stu-id="9f12d-123">The #3 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_4`|<span data-ttu-id="9f12d-124">O registro de pilha #4 no processador x86 de FP.</span><span class="sxs-lookup"><span data-stu-id="9f12d-124">The #4 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_5`|<span data-ttu-id="9f12d-125">O registro de pilha #5 no processador x86 de FP.</span><span class="sxs-lookup"><span data-stu-id="9f12d-125">The #5 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_6`|<span data-ttu-id="9f12d-126">O registro de pilha #6 no processador x86 de FP.</span><span class="sxs-lookup"><span data-stu-id="9f12d-126">The #6 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_7`|<span data-ttu-id="9f12d-127">O registro de pilha #7 no processador x86 de FP.</span><span class="sxs-lookup"><span data-stu-id="9f12d-127">The #7 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_AMD64_RIP`|<span data-ttu-id="9f12d-128">O registro de ponteiro de instrução no processador AMD64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-128">The instruction pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RSP`|<span data-ttu-id="9f12d-129">O registro de ponteiro de pilha no processador AMD64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-129">The stack pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RBP`|<span data-ttu-id="9f12d-130">O registro de ponteiro de base no processador AMD64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-130">The base pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RAX`|<span data-ttu-id="9f12d-131">O registro de dados A no processador AMD64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-131">The A data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RCX`|<span data-ttu-id="9f12d-132">O registro de dados C no processador AMD64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-132">The C data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RDX`|<span data-ttu-id="9f12d-133">O registro de dados D no processador AMD64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-133">The D data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RBX`|<span data-ttu-id="9f12d-134">O registro de dados B no processador AMD64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-134">The B data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RSI`|<span data-ttu-id="9f12d-135">O registro de índice de origem no processador AMD64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-135">The source index register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RDI`|<span data-ttu-id="9f12d-136">O registro de índice de destino no processador AMD64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-136">The destination index register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R8`|<span data-ttu-id="9f12d-137">O registro de dados #8 no processador AMD64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-137">The #8 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R9`|<span data-ttu-id="9f12d-138">O registro de dados #9 no processador AMD64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-138">The #9 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R10`|<span data-ttu-id="9f12d-139">O registro de dados #10 no processador AMD64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-139">The #10 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R11`|<span data-ttu-id="9f12d-140">O registro de dados #11 no processador AMD64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-140">The #11 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R12`|<span data-ttu-id="9f12d-141">O registro de dados #12 no processador AMD64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-141">The #12 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R13`|<span data-ttu-id="9f12d-142">O registro de dados #13 no processador AMD64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-142">The #13 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R14`|<span data-ttu-id="9f12d-143">O registro de dados #14 no processador AMD64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-143">The #14 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R15`|<span data-ttu-id="9f12d-144">O registro de dados #15 no processador AMD64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-144">The #15 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM0`|<span data-ttu-id="9f12d-145">O registro de multimídia #0 no processador AMD64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-145">The #0 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM1`|<span data-ttu-id="9f12d-146">O registro de multimídia #1 no processador AMD64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-146">The #1 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM2`|<span data-ttu-id="9f12d-147">O registro de multimídia #2 no processador AMD64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-147">The #2 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM3`|<span data-ttu-id="9f12d-148">O registro de multimídia #3 no processador AMD64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-148">The #3 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM4`|<span data-ttu-id="9f12d-149">O registro de multimídia #4 no processador AMD64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-149">The #4 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM5`|<span data-ttu-id="9f12d-150">O registro de multimídia #5 no processador AMD64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-150">The #5 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM6`|<span data-ttu-id="9f12d-151">O registro de multimídia #6 no processador AMD64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-151">The #6 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM7`|<span data-ttu-id="9f12d-152">O registro de multimídia #7 no processador AMD64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-152">The #7 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM8`|<span data-ttu-id="9f12d-153">O registro de multimídia #8 no processador AMD64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-153">The #8 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM9`|<span data-ttu-id="9f12d-154">O registro de multimídia #9 no processador AMD64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-154">The #9 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM10`|<span data-ttu-id="9f12d-155">O registro de multimídia #10 no processador AMD64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-155">The #10 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM11`|<span data-ttu-id="9f12d-156">O registro de multimídia #11 no processador AMD64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-156">The #11 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM12`|<span data-ttu-id="9f12d-157">O registro de multimídia #12 no processador AMD64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-157">The #12 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM13`|<span data-ttu-id="9f12d-158">O registro de multimídia #13 no processador AMD64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-158">The #13 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM14`|<span data-ttu-id="9f12d-159">O registro de multimídia #14 no processador AMD64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-159">The #14 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM15`|<span data-ttu-id="9f12d-160">O registro de multimídia #15 no processador AMD64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-160">The #15 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_IA64_BSP`|<span data-ttu-id="9f12d-161">O registro de ponteiro de pilha no processador IA-64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-161">The stack pointer register on the IA-64 processor.</span></span>|  
|`REGISTER_IA64_R0`|<span data-ttu-id="9f12d-162">O registro de dados #0 no processador IA-64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-162">The #0 data register on the IA-64 processor.</span></span>|  
|`REGISTER_IA64_F0`|<span data-ttu-id="9f12d-163">O registro de dados de FP #0 no processador IA-64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-163">The #0 FP data register on the IA-64 processor.</span></span>|  
|`REGISTER_ARM_PC`|<span data-ttu-id="9f12d-164">O registro do contador de programa (R15) no processador ARM.</span><span class="sxs-lookup"><span data-stu-id="9f12d-164">The program counter register (R15) on the ARM processor.</span></span>|  
|`REGISTER_ARM_SP`|<span data-ttu-id="9f12d-165">O registro do ponteiro de pilha (R13) no processador ARM.</span><span class="sxs-lookup"><span data-stu-id="9f12d-165">The stack pointer register (R13) on the ARM processor.</span></span>|  
|`REGISTER_ARM_R0`|<span data-ttu-id="9f12d-166">Registro de dados R0 no processador ARM.</span><span class="sxs-lookup"><span data-stu-id="9f12d-166">Data register R0 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R1`|<span data-ttu-id="9f12d-167">Registro de dados R1 no processador ARM.</span><span class="sxs-lookup"><span data-stu-id="9f12d-167">Data register R1 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R2`|<span data-ttu-id="9f12d-168">Registro de dados R2 no processador ARM.</span><span class="sxs-lookup"><span data-stu-id="9f12d-168">Data register R2 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R3`|<span data-ttu-id="9f12d-169">Registro de dados R3 no processador ARM.</span><span class="sxs-lookup"><span data-stu-id="9f12d-169">Data register R3 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R4`|<span data-ttu-id="9f12d-170">Registro R4 no processador ARM.</span><span class="sxs-lookup"><span data-stu-id="9f12d-170">Register R4 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R5`|<span data-ttu-id="9f12d-171">Registro R5 no processador ARM.</span><span class="sxs-lookup"><span data-stu-id="9f12d-171">Register R5 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R6`|<span data-ttu-id="9f12d-172">Registro R6 no processador ARM.</span><span class="sxs-lookup"><span data-stu-id="9f12d-172">Register R6 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R7`|<span data-ttu-id="9f12d-173">O registro R7 (o ponteiro de quadro THuMB) no processador ARM.</span><span class="sxs-lookup"><span data-stu-id="9f12d-173">Register R7 (the THUMB frame pointer) on the ARM processor.</span></span>|  
|`REGISTER_ARM_R8`|<span data-ttu-id="9f12d-174">Registro R8 no processador ARM.</span><span class="sxs-lookup"><span data-stu-id="9f12d-174">Register R8 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R9`|<span data-ttu-id="9f12d-175">Registro R9 no processador ARM.</span><span class="sxs-lookup"><span data-stu-id="9f12d-175">Register R9 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R10`|<span data-ttu-id="9f12d-176">Registro R10 no processador ARM.</span><span class="sxs-lookup"><span data-stu-id="9f12d-176">Register R10 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R11`|<span data-ttu-id="9f12d-177">O ponteiro de quadro no processador ARM.</span><span class="sxs-lookup"><span data-stu-id="9f12d-177">The frame pointer on the ARM processor.</span></span>|  
|`REGISTER_ARM_R12`|<span data-ttu-id="9f12d-178">Registro R12 no processador ARM.</span><span class="sxs-lookup"><span data-stu-id="9f12d-178">Register R12 on the ARM processor.</span></span>|  
|`REGISTER_ARM_LR`|<span data-ttu-id="9f12d-179">O registro de vínculo (R14) no processador ARM.</span><span class="sxs-lookup"><span data-stu-id="9f12d-179">The link register (R14) on the ARM processor.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f12d-180">Comentários</span><span class="sxs-lookup"><span data-stu-id="9f12d-180">Remarks</span></span>  
 <span data-ttu-id="9f12d-181">Existem 128 registros de dados de uso geral e 128 registros de dados de ponto flutuante no processador IA-64, porém, apenas os valores `REGISTER_IA64_R0` e `REGISTER_IA64_F0` são fornecidos.</span><span class="sxs-lookup"><span data-stu-id="9f12d-181">There are 128 general-purpose data registers and 128 floating-point data registers on the IA-64 processor, but only values `REGISTER_IA64_R0` and `REGISTER_IA64_F0` are provided.</span></span> <span data-ttu-id="9f12d-182">Os outros valores podem ser determinados da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="9f12d-182">The other values can be determined as follows:</span></span>  
  
- <span data-ttu-id="9f12d-183">Some o número do registro ao `REGISTER_IA64_R0` para os valores `REGISTER_IA64_R1` até `REGISTER_IA64_R127`, que correspondem ao registro de dados #1 até o registro de dados #127 no processador IA-64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-183">Add the register number to `REGISTER_IA64_R0` for values `REGISTER_IA64_R1` through `REGISTER_IA64_R127`, which correspond to the #1 data register through the #127 data register on the IA-64 processor.</span></span>  
  
- <span data-ttu-id="9f12d-184">Some o número do registro ao `REGISTER_IA64_F0` para os valores `REGISTER_IA64_F1` até `REGISTER_IA64_F127`, que correspondem ao registro de dados de FP #1 até o registro de dados de FP #127 no processador IA-64.</span><span class="sxs-lookup"><span data-stu-id="9f12d-184">Add the register number to `REGISTER_IA64_F0` for values `REGISTER_IA64_F1` through `REGISTER_IA64_F127`, which correspond to the #1 FP data register through the #127 FP data register on the IA-64 processor.</span></span>  
  
 <span data-ttu-id="9f12d-185">Por exemplo, se for necessário especificar o registro de dados #83 no processador IA-64, use `REGISTER_IA64_R0` + 83.</span><span class="sxs-lookup"><span data-stu-id="9f12d-185">For example, if you need to specify the #83 data register on the IA-64 processor, use `REGISTER_IA64_R0` + 83.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f12d-186">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9f12d-186">Requirements</span></span>  
 <span data-ttu-id="9f12d-187">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f12d-187">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f12d-188">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9f12d-188">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f12d-189">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f12d-189">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f12d-190">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f12d-190">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f12d-191">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9f12d-191">See also</span></span>

- [<span data-ttu-id="9f12d-192">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="9f12d-192">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
