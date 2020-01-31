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
ms.openlocfilehash: 39833b689f28437b4241d9cb15fb4a92b2f9bcc3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791368"
---
# <a name="icordebugthread4getblockingobjects-method"></a><span data-ttu-id="280f7-102">Método ICorDebugThread4::GetBlockingObjects</span><span class="sxs-lookup"><span data-stu-id="280f7-102">ICorDebugThread4::GetBlockingObjects Method</span></span>
<span data-ttu-id="280f7-103">Fornece uma enumeração ordenada de estruturas [CorDebugBlockingObject](cordebugblockingobject-structure.md) que fornecem informações de bloqueio de thread.</span><span class="sxs-lookup"><span data-stu-id="280f7-103">Provides an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="280f7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="280f7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
## <a name="parameters"></a><span data-ttu-id="280f7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="280f7-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="280f7-106">fora Um ponteiro para uma enumeração ordenada de estruturas [CorDebugBlockingObject](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="280f7-106">[out] A pointer to an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="280f7-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="280f7-107">Remarks</span></span>  
 <span data-ttu-id="280f7-108">O primeiro elemento na enumeração retornada corresponde à primeira estrutura que está bloqueando o thread.</span><span class="sxs-lookup"><span data-stu-id="280f7-108">The first element in the returned enumeration corresponds to the first structure that is blocking the thread.</span></span> <span data-ttu-id="280f7-109">O segundo elemento corresponde a um item de bloqueio que é encontrado durante a execução de uma APC (chamada de procedimento assíncrono) quando bloqueado no primeiro e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="280f7-109">The second element corresponds to a blocking item that is encountered while running an asynchronous procedure call (APC) when blocked on the first, and so on.</span></span>  
  
 <span data-ttu-id="280f7-110">A enumeração é válida somente pela duração do estado atual sincronizado.</span><span class="sxs-lookup"><span data-stu-id="280f7-110">The enumeration is valid only for the duration of the current synchronized state.</span></span>  
  
 <span data-ttu-id="280f7-111">Esse método deve ser chamado enquanto o depurado estiver em um estado sincronizado.</span><span class="sxs-lookup"><span data-stu-id="280f7-111">This method must be called while the debuggee is in a synchronized state.</span></span>  
  
 <span data-ttu-id="280f7-112">Se `ppBlockingObjectEnum` não for um ponteiro válido, o resultado será indefinido.</span><span class="sxs-lookup"><span data-stu-id="280f7-112">If `ppBlockingObjectEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="280f7-113">Se um thread for bloqueado e o erro não puder ser determinado, o método retornará um HRESULT que indica falha; caso contrário, ele retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="280f7-113">If a thread is blocked and the error cannot be determined, the method returns an HRESULT that indicates failure; otherwise, it returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="280f7-114">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="280f7-114">Requirements</span></span>  
 <span data-ttu-id="280f7-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="280f7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="280f7-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="280f7-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="280f7-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="280f7-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="280f7-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="280f7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="280f7-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="280f7-119">See also</span></span>

- [<span data-ttu-id="280f7-120">Interface ICorDebugThread4</span><span class="sxs-lookup"><span data-stu-id="280f7-120">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="280f7-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="280f7-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="280f7-122">Depuração</span><span class="sxs-lookup"><span data-stu-id="280f7-122">Debugging</span></span>](index.md)
