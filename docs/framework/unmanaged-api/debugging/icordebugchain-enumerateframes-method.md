---
title: "Método ICorDebugChain::EnumerateFrames"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.EnumerateFrames
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::EnumerateFrames method
helpviewer_keywords:
- EnumerateFrames method [.NET Framework debugging]
- ICorDebugChain::EnumerateFrames method [.NET Framework debugging]
ms.assetid: 9fcefa98-750d-4168-8915-8173a43accf2
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 87e2fbc0a4ca9d97ac7e57234383ebd8cee56211
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugchainenumerateframes-method"></a><span data-ttu-id="e65e4-102">Método ICorDebugChain::EnumerateFrames</span><span class="sxs-lookup"><span data-stu-id="e65e4-102">ICorDebugChain::EnumerateFrames Method</span></span>
<span data-ttu-id="e65e4-103">Obtém um enumerador que contém todos os quadros de pilha gerenciada na cadeia, começando com o quadro mais recente.</span><span class="sxs-lookup"><span data-stu-id="e65e4-103">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e65e4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e65e4-104">Syntax</span></span>  
  
```  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e65e4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e65e4-105">Parameters</span></span>  
 `ppFrames`  
 <span data-ttu-id="e65e4-106">[out] Um ponteiro para o endereço de um objeto de ICorDebugFrameEnum que é o enumerador para os quadros de pilha.</span><span class="sxs-lookup"><span data-stu-id="e65e4-106">[out] A pointer to the address of an ICorDebugFrameEnum object that is the enumerator for the stack frames.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e65e4-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="e65e4-107">Remarks</span></span>  
 <span data-ttu-id="e65e4-108">A cadeia representa a pilha de chamadas físico para o thread.</span><span class="sxs-lookup"><span data-stu-id="e65e4-108">The chain represents the physical call stack for the thread.</span></span>  
  
 <span data-ttu-id="e65e4-109">O `EnumerateFrames` método deve ser chamado somente para gerenciado cadeias.</span><span class="sxs-lookup"><span data-stu-id="e65e4-109">The `EnumerateFrames` method should be called only for managed chains.</span></span> <span data-ttu-id="e65e4-110">A API de depuração não fornece métodos para a obtenção de quadros contidos nas cadeias de não gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="e65e4-110">The debugging API does not provide methods for obtaining frames contained in unmanaged chains.</span></span> <span data-ttu-id="e65e4-111">O depurador deve usar outro meio para obter essas informações.</span><span class="sxs-lookup"><span data-stu-id="e65e4-111">The debugger must use other means to obtain this information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e65e4-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e65e4-112">Requirements</span></span>  
 <span data-ttu-id="e65e4-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e65e4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e65e4-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e65e4-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e65e4-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e65e4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e65e4-116">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e65e4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
