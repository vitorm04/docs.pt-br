---
title: Método ICorDebugThread4::GetBlockingObjects
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.GetBlockingObjects Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::GetBlockingObjects
helpviewer_keywords:
- GetBlockingObjects method [.NET Framework debugging]
- ICorDebugThread4::GetBlockingObjects method [.NET Framework debugging]
ms.assetid: a7e6c54e-7be9-4e52-bbb4-95f52458e8e4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d83f9c0b187ad8b2955bc12ff168e0c4f26b909
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765221"
---
# <a name="icordebugthread4getblockingobjects-method"></a><span data-ttu-id="a2cb3-102">Método ICorDebugThread4::GetBlockingObjects</span><span class="sxs-lookup"><span data-stu-id="a2cb3-102">ICorDebugThread4::GetBlockingObjects Method</span></span>
<span data-ttu-id="a2cb3-103">Fornece uma enumeração ordenada de [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) estruturas que fornecem informações de bloqueio do thread.</span><span class="sxs-lookup"><span data-stu-id="a2cb3-103">Provides an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2cb3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a2cb3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2cb3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a2cb3-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="a2cb3-106">[out] Um ponteiro para uma enumeração ordenada de [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) estruturas.</span><span class="sxs-lookup"><span data-stu-id="a2cb3-106">[out] A pointer to an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2cb3-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="a2cb3-107">Remarks</span></span>  
 <span data-ttu-id="a2cb3-108">O primeiro elemento na enumeração retornada corresponde à primeira estrutura que está bloqueando o thread.</span><span class="sxs-lookup"><span data-stu-id="a2cb3-108">The first element in the returned enumeration corresponds to the first structure that is blocking the thread.</span></span> <span data-ttu-id="a2cb3-109">O segundo elemento corresponde a um item de bloqueio é encontrado durante a execução de uma chamada de procedimento assíncrono (APC) quando bloqueado na primeira e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="a2cb3-109">The second element corresponds to a blocking item that is encountered while running an asynchronous procedure call (APC) when blocked on the first, and so on.</span></span>  
  
 <span data-ttu-id="a2cb3-110">A enumeração é válida apenas para a duração do estado atual de sincronizado.</span><span class="sxs-lookup"><span data-stu-id="a2cb3-110">The enumeration is valid only for the duration of the current synchronized state.</span></span>  
  
 <span data-ttu-id="a2cb3-111">Esse método deve ser chamado enquanto o elemento a ser depurado está em um estado sincronizado.</span><span class="sxs-lookup"><span data-stu-id="a2cb3-111">This method must be called while the debuggee is in a synchronized state.</span></span>  
  
 <span data-ttu-id="a2cb3-112">Se `ppBlockingObjectEnum` não for um ponteiro válido, o resultado será indefinido.</span><span class="sxs-lookup"><span data-stu-id="a2cb3-112">If `ppBlockingObjectEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="a2cb3-113">Se um thread estiver bloqueado e o erro não pode ser determinado, o método retorna um HRESULT que indica falha; Caso contrário, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="a2cb3-113">If a thread is blocked and the error cannot be determined, the method returns an HRESULT that indicates failure; otherwise, it returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2cb3-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a2cb3-114">Requirements</span></span>  
 <span data-ttu-id="a2cb3-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2cb3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2cb3-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a2cb3-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2cb3-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2cb3-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2cb3-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2cb3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2cb3-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a2cb3-119">See also</span></span>

- [<span data-ttu-id="a2cb3-120">Interface ICorDebugThread4</span><span class="sxs-lookup"><span data-stu-id="a2cb3-120">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [<span data-ttu-id="a2cb3-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a2cb3-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="a2cb3-122">Depuração</span><span class="sxs-lookup"><span data-stu-id="a2cb3-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
