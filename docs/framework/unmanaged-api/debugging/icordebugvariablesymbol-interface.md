---
title: Interface ICorDebugVariableSymbol
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9822a3403c6ff738f7a6556a35cb383426575cb9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582585"
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="9b2e8-102">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="9b2e8-102">ICorDebugVariableSymbol Interface</span></span>
<span data-ttu-id="9b2e8-103">Recupera as informações de símbolo de depuração de uma variável.</span><span class="sxs-lookup"><span data-stu-id="9b2e8-103">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9b2e8-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="9b2e8-104">Methods</span></span>  
  
|<span data-ttu-id="9b2e8-105">Método</span><span class="sxs-lookup"><span data-stu-id="9b2e8-105">Method</span></span>|<span data-ttu-id="9b2e8-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="9b2e8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9b2e8-107">Método GetName</span><span class="sxs-lookup"><span data-stu-id="9b2e8-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="9b2e8-108">Obtém o nome de uma variável.</span><span class="sxs-lookup"><span data-stu-id="9b2e8-108">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="9b2e8-109">Método GetSize</span><span class="sxs-lookup"><span data-stu-id="9b2e8-109">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="9b2e8-110">Obtém o tamanho de uma variável em bytes.</span><span class="sxs-lookup"><span data-stu-id="9b2e8-110">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="9b2e8-111">Método GetSlotIndex</span><span class="sxs-lookup"><span data-stu-id="9b2e8-111">GetSlotIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="9b2e8-112">Obtém o índice de slot gerenciado de uma variável local.</span><span class="sxs-lookup"><span data-stu-id="9b2e8-112">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="9b2e8-113">Método GetValue</span><span class="sxs-lookup"><span data-stu-id="9b2e8-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="9b2e8-114">Obtém o valor de uma variável como uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="9b2e8-114">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="9b2e8-115">Método SetValue</span><span class="sxs-lookup"><span data-stu-id="9b2e8-115">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="9b2e8-116">Atribui o valor de uma matriz de bytes a uma variável.</span><span class="sxs-lookup"><span data-stu-id="9b2e8-116">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b2e8-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="9b2e8-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b2e8-118">Essa interface só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9b2e8-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="9b2e8-119">Se você implementar essa interface para cenários de ICorDebug fora do .NET nativo, o common language runtime irá ignorar essa interface.</span><span class="sxs-lookup"><span data-stu-id="9b2e8-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b2e8-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9b2e8-120">Requirements</span></span>  
 <span data-ttu-id="9b2e8-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b2e8-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b2e8-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b2e8-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b2e8-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b2e8-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b2e8-124">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b2e8-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b2e8-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9b2e8-125">See also</span></span>
- [<span data-ttu-id="9b2e8-126">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="9b2e8-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="9b2e8-127">Depuração</span><span class="sxs-lookup"><span data-stu-id="9b2e8-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
