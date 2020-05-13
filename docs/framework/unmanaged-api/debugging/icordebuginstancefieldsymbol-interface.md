---
title: Interface ICorDebugInstanceFieldSymbol
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
ms.openlocfilehash: 092f2a8acdffa9f91176bdf0ca10b8db9cff6d37
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209923"
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="91638-102">Interface ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="91638-102">ICorDebugInstanceFieldSymbol Interface</span></span>
<span data-ttu-id="91638-103">Representa as informações de símbolo de depuração de um campo de instância.</span><span class="sxs-lookup"><span data-stu-id="91638-103">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="91638-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="91638-104">Methods</span></span>  
  
|<span data-ttu-id="91638-105">Método</span><span class="sxs-lookup"><span data-stu-id="91638-105">Method</span></span>|<span data-ttu-id="91638-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="91638-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="91638-107">Método GetName</span><span class="sxs-lookup"><span data-stu-id="91638-107">GetName Method</span></span>](icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="91638-108">Obtém o nome do campo de instância.</span><span class="sxs-lookup"><span data-stu-id="91638-108">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="91638-109">Método GetOffset</span><span class="sxs-lookup"><span data-stu-id="91638-109">GetOffset Method</span></span>](icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="91638-110">Obtém o deslocamento em bytes deste campo de instância em sua classe pai.</span><span class="sxs-lookup"><span data-stu-id="91638-110">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="91638-111">Método GetSize</span><span class="sxs-lookup"><span data-stu-id="91638-111">GetSize Method</span></span>](icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="91638-112">Obtém o tamanho em bytes do campo de instância.</span><span class="sxs-lookup"><span data-stu-id="91638-112">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91638-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="91638-113">Remarks</span></span>  
 <span data-ttu-id="91638-114">A `ICorDebugInstanceFieldSymbol` interface é usada para recuperar as informações de símbolo de depuração para um campo de instância.</span><span class="sxs-lookup"><span data-stu-id="91638-114">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="91638-115">Essa interface está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="91638-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="91638-116">Se você implementar essa interface para cenários ICorDebug fora do .NET Native, o Common Language Runtime ignorará essa interface.</span><span class="sxs-lookup"><span data-stu-id="91638-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91638-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="91638-117">Requirements</span></span>  
 <span data-ttu-id="91638-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91638-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91638-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="91638-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91638-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91638-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91638-121">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91638-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91638-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="91638-122">See also</span></span>

- [<span data-ttu-id="91638-123">Interface ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="91638-123">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="91638-124">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="91638-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="91638-125">Depuração</span><span class="sxs-lookup"><span data-stu-id="91638-125">Debugging</span></span>](index.md)
