---
title: Método ICorDebugChain::EnumerateFrames
ms.date: 03/30/2017
api_name:
- ICorDebugChain.EnumerateFrames
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::EnumerateFrames method
helpviewer_keywords:
- EnumerateFrames method [.NET Framework debugging]
- ICorDebugChain::EnumerateFrames method [.NET Framework debugging]
ms.assetid: 9fcefa98-750d-4168-8915-8173a43accf2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d408f317b546fb7e8314e904e6f5ad9e6296ae6d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403260"
---
# <a name="icordebugchainenumerateframes-method"></a><span data-ttu-id="f12e9-102">Método ICorDebugChain::EnumerateFrames</span><span class="sxs-lookup"><span data-stu-id="f12e9-102">ICorDebugChain::EnumerateFrames Method</span></span>
<span data-ttu-id="f12e9-103">Obtém um enumerador que contém todos os quadros de pilha gerenciada na cadeia, começando com o quadro mais recente.</span><span class="sxs-lookup"><span data-stu-id="f12e9-103">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f12e9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f12e9-104">Syntax</span></span>  
  
```  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f12e9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f12e9-105">Parameters</span></span>  
 `ppFrames`  
 <span data-ttu-id="f12e9-106">[out] Um ponteiro para o endereço de um objeto de ICorDebugFrameEnum que é o enumerador para os quadros de pilha.</span><span class="sxs-lookup"><span data-stu-id="f12e9-106">[out] A pointer to the address of an ICorDebugFrameEnum object that is the enumerator for the stack frames.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f12e9-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="f12e9-107">Remarks</span></span>  
 <span data-ttu-id="f12e9-108">A cadeia representa a pilha de chamadas físico para o thread.</span><span class="sxs-lookup"><span data-stu-id="f12e9-108">The chain represents the physical call stack for the thread.</span></span>  
  
 <span data-ttu-id="f12e9-109">O `EnumerateFrames` método deve ser chamado somente para gerenciado cadeias.</span><span class="sxs-lookup"><span data-stu-id="f12e9-109">The `EnumerateFrames` method should be called only for managed chains.</span></span> <span data-ttu-id="f12e9-110">A API de depuração não fornece métodos para a obtenção de quadros contidos nas cadeias de não gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="f12e9-110">The debugging API does not provide methods for obtaining frames contained in unmanaged chains.</span></span> <span data-ttu-id="f12e9-111">O depurador deve usar outro meio para obter essas informações.</span><span class="sxs-lookup"><span data-stu-id="f12e9-111">The debugger must use other means to obtain this information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f12e9-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f12e9-112">Requirements</span></span>  
 <span data-ttu-id="f12e9-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f12e9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f12e9-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f12e9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f12e9-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f12e9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f12e9-116">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f12e9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
