---
title: Método ICorDebugILFrame::GetIP
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::GetIP method [.NET Framework debugging]
ms.assetid: 18217ba1-1776-4297-a3b9-f77e64b0fead
topic_type:
- apiref
ms.openlocfilehash: 7e1605eede55360e72d65da6744bc1dcce4f107f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130987"
---
# <a name="icordebugilframegetip-method"></a><span data-ttu-id="64a5b-102">Método ICorDebugILFrame::GetIP</span><span class="sxs-lookup"><span data-stu-id="64a5b-102">ICorDebugILFrame::GetIP Method</span></span>
<span data-ttu-id="64a5b-103">Obtém o valor do ponteiro de instrução e um valor de combinação de bits que descreve como o valor do ponteiro de instrução foi obtido.</span><span class="sxs-lookup"><span data-stu-id="64a5b-103">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64a5b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="64a5b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,   
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64a5b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="64a5b-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="64a5b-106">fora O valor do ponteiro de instrução.</span><span class="sxs-lookup"><span data-stu-id="64a5b-106">[out] The value of the instruction pointer.</span></span>  
  
 `pMappingResult`  
 <span data-ttu-id="64a5b-107">fora Um ponteiro para uma combinação de bits de bit que descreve os valores de enumeração CorDebugMappingResult que descrevem como o valor do ponteiro de instrução foi obtido.</span><span class="sxs-lookup"><span data-stu-id="64a5b-107">[out] A pointer to a bitwise combination of the CorDebugMappingResult enumeration values that describe how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64a5b-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="64a5b-108">Remarks</span></span>  
 <span data-ttu-id="64a5b-109">O valor do ponteiro de instrução é o deslocamento do registro de ativação no código MSIL (Microsoft Intermediate Language) da função.</span><span class="sxs-lookup"><span data-stu-id="64a5b-109">The value of the instruction pointer is the stack frame's offset into the function's Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="64a5b-110">Se o registro de ativação estiver ativo, esse endereço será a próxima instrução a ser executada.</span><span class="sxs-lookup"><span data-stu-id="64a5b-110">If the stack frame is active, this address is the next instruction to execute.</span></span> <span data-ttu-id="64a5b-111">Se o registro de ativação não estiver ativo, esse endereço será a próxima instrução a ser executada quando o quadro de pilha for reativado.</span><span class="sxs-lookup"><span data-stu-id="64a5b-111">If the stack frame is not active, this address is the next instruction to execute when the stack frame is reactivated.</span></span>  
  
 <span data-ttu-id="64a5b-112">Se esse quadro for um quadro compilado JIT (just-in-time), o valor do ponteiro de instrução será determinado pelo mapeamento retroativo do ponteiro de instrução nativa real, de modo que o valor pode ser apenas aproximado.</span><span class="sxs-lookup"><span data-stu-id="64a5b-112">If this frame is a just-in-time (JIT) compiled frame, the value of the instruction pointer will be determined by mapping backwards from the actual native instruction pointer, so the value may be only approximate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64a5b-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="64a5b-113">Requirements</span></span>  
 <span data-ttu-id="64a5b-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64a5b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64a5b-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="64a5b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64a5b-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64a5b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64a5b-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64a5b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
