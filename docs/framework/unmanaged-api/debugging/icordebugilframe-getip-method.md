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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a7b8985e7580282d0e38205f9b1d6078f86cee6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988605"
---
# <a name="icordebugilframegetip-method"></a><span data-ttu-id="28666-102">Método ICorDebugILFrame::GetIP</span><span class="sxs-lookup"><span data-stu-id="28666-102">ICorDebugILFrame::GetIP Method</span></span>
<span data-ttu-id="28666-103">Obtém o valor do ponteiro de instrução e um valor de combinação bit a bit que descreve como o valor do ponteiro de instrução foi obtido.</span><span class="sxs-lookup"><span data-stu-id="28666-103">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28666-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="28666-104">Syntax</span></span>  
  
```  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,   
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28666-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="28666-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="28666-106">[out] O valor do ponteiro de instrução.</span><span class="sxs-lookup"><span data-stu-id="28666-106">[out] The value of the instruction pointer.</span></span>  
  
 `pMappingResult`  
 <span data-ttu-id="28666-107">[out] Um ponteiro para uma combinação bit a bit dos valores de enumeração CorDebugMappingResult que descrevem como o valor do ponteiro de instrução foi obtido.</span><span class="sxs-lookup"><span data-stu-id="28666-107">[out] A pointer to a bitwise combination of the CorDebugMappingResult enumeration values that describe how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28666-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="28666-108">Remarks</span></span>  
 <span data-ttu-id="28666-109">O valor do ponteiro de instrução é o deslocamento do quadro de pilha no código da função Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="28666-109">The value of the instruction pointer is the stack frame's offset into the function's Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="28666-110">Se o quadro de pilhas estiver ativo, esse endereço é a próxima instrução a executar.</span><span class="sxs-lookup"><span data-stu-id="28666-110">If the stack frame is active, this address is the next instruction to execute.</span></span> <span data-ttu-id="28666-111">Se o quadro de pilha não estiver ativo, esse endereço é a próxima instrução a ser executado quando o quadro de pilha for reativado.</span><span class="sxs-lookup"><span data-stu-id="28666-111">If the stack frame is not active, this address is the next instruction to execute when the stack frame is reactivated.</span></span>  
  
 <span data-ttu-id="28666-112">Se este quadro é um quadro compilado do just-in-time (JIT), o valor do ponteiro de instrução será determinado pelo mapeamento com versões anteriores do ponteiro de instrução de nativa real, portanto, o valor pode ser apenas aproximado.</span><span class="sxs-lookup"><span data-stu-id="28666-112">If this frame is a just-in-time (JIT) compiled frame, the value of the instruction pointer will be determined by mapping backwards from the actual native instruction pointer, so the value may be only approximate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28666-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="28666-113">Requirements</span></span>  
 <span data-ttu-id="28666-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28666-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28666-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="28666-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="28666-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28666-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28666-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28666-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
