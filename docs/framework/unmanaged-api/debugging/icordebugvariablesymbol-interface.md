---
title: Interface ICorDebugVariableSymbol
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3fb2538894184c19bc107ce52cbef3ac86a97345
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967978"
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="82b76-102">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="82b76-102">ICorDebugVariableSymbol Interface</span></span>
<span data-ttu-id="82b76-103">Recupera as informações de símbolo de depuração para uma variável.</span><span class="sxs-lookup"><span data-stu-id="82b76-103">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="82b76-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="82b76-104">Methods</span></span>  
  
|<span data-ttu-id="82b76-105">Método</span><span class="sxs-lookup"><span data-stu-id="82b76-105">Method</span></span>|<span data-ttu-id="82b76-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="82b76-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="82b76-107">Método GetName</span><span class="sxs-lookup"><span data-stu-id="82b76-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="82b76-108">Obtém o nome de uma variável.</span><span class="sxs-lookup"><span data-stu-id="82b76-108">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="82b76-109">Método GetSize</span><span class="sxs-lookup"><span data-stu-id="82b76-109">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="82b76-110">Obtém o tamanho de uma variável em bytes.</span><span class="sxs-lookup"><span data-stu-id="82b76-110">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="82b76-111">Método GetSlotIndex</span><span class="sxs-lookup"><span data-stu-id="82b76-111">GetSlotIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="82b76-112">Obtém o índice de slot gerenciado de uma variável local.</span><span class="sxs-lookup"><span data-stu-id="82b76-112">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="82b76-113">Método GetValue</span><span class="sxs-lookup"><span data-stu-id="82b76-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="82b76-114">Obtém o valor de uma variável como uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="82b76-114">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="82b76-115">Método SetValue</span><span class="sxs-lookup"><span data-stu-id="82b76-115">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="82b76-116">Atribui o valor de uma matriz de bytes a uma variável.</span><span class="sxs-lookup"><span data-stu-id="82b76-116">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82b76-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="82b76-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82b76-118">Essa interface está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="82b76-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="82b76-119">Se você implementar essa interface para cenários ICorDebug fora do .NET Native, o Common Language Runtime ignorará essa interface.</span><span class="sxs-lookup"><span data-stu-id="82b76-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82b76-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="82b76-120">Requirements</span></span>  
 <span data-ttu-id="82b76-121">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82b76-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82b76-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="82b76-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82b76-123">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82b76-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82b76-124">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82b76-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82b76-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82b76-125">See also</span></span>

- [<span data-ttu-id="82b76-126">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="82b76-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="82b76-127">Depuração</span><span class="sxs-lookup"><span data-stu-id="82b76-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
