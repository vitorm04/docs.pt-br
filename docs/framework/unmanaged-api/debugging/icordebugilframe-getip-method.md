---
title: "Método ICorDebugILFrame::GetIP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.GetIP
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::GetIP method [.NET Framework debugging]
ms.assetid: 18217ba1-1776-4297-a3b9-f77e64b0fead
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6f1ea9ad653deeaaa22944517ba5cbdb2f39c6d4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugilframegetip-method"></a><span data-ttu-id="c8a9a-102">Método ICorDebugILFrame::GetIP</span><span class="sxs-lookup"><span data-stu-id="c8a9a-102">ICorDebugILFrame::GetIP Method</span></span>
<span data-ttu-id="c8a9a-103">Obtém o valor do ponteiro de instrução e um valor de combinação bit a bit que descreve como o valor do ponteiro de instrução foi obtido.</span><span class="sxs-lookup"><span data-stu-id="c8a9a-103">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8a9a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c8a9a-104">Syntax</span></span>  
  
```  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,   
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c8a9a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c8a9a-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="c8a9a-106">[out] O valor do ponteiro de instrução.</span><span class="sxs-lookup"><span data-stu-id="c8a9a-106">[out] The value of the instruction pointer.</span></span>  
  
 `pMappingResult`  
 <span data-ttu-id="c8a9a-107">[out] Um ponteiro para uma combinação bit a bit dos valores de enumeração CorDebugMappingResult que descrevem como o valor do ponteiro de instrução foi obtido.</span><span class="sxs-lookup"><span data-stu-id="c8a9a-107">[out] A pointer to a bitwise combination of the CorDebugMappingResult enumeration values that describe how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8a9a-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="c8a9a-108">Remarks</span></span>  
 <span data-ttu-id="c8a9a-109">O valor do ponteiro de instrução é o deslocamento do quadro de pilha em código da função Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="c8a9a-109">The value of the instruction pointer is the stack frame's offset into the function's Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="c8a9a-110">Se o quadro de pilhas estiver ativo, esse endereço é a próxima instrução a executar.</span><span class="sxs-lookup"><span data-stu-id="c8a9a-110">If the stack frame is active, this address is the next instruction to execute.</span></span> <span data-ttu-id="c8a9a-111">Se o quadro de pilha não estiver ativo, esse endereço é a próxima instrução a ser executada quando o quadro de pilhas é reativado.</span><span class="sxs-lookup"><span data-stu-id="c8a9a-111">If the stack frame is not active, this address is the next instruction to execute when the stack frame is reactivated.</span></span>  
  
 <span data-ttu-id="c8a9a-112">Se este quadro é um quadro compilado do just-in-time (JIT), o valor do ponteiro de instrução será determinado pelo mapeamento com versões anteriores de ponteiro de instrução nativos real, portanto, o valor pode ser apenas aproximado.</span><span class="sxs-lookup"><span data-stu-id="c8a9a-112">If this frame is a just-in-time (JIT) compiled frame, the value of the instruction pointer will be determined by mapping backwards from the actual native instruction pointer, so the value may be only approximate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8a9a-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c8a9a-113">Requirements</span></span>  
 <span data-ttu-id="c8a9a-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8a9a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8a9a-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c8a9a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8a9a-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8a9a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8a9a-117">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8a9a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
