---
title: Método ICorDebugAssembly3::GetContainerAssembly
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ddae1da8b07afff6ade28fb6dcae942cddd8c2e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471609"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a><span data-ttu-id="84f40-102">Método ICorDebugAssembly3::GetContainerAssembly</span><span class="sxs-lookup"><span data-stu-id="84f40-102">ICorDebugAssembly3::GetContainerAssembly Method</span></span>
<span data-ttu-id="84f40-103">Retorna o assembly do contêiner desse objeto `ICorDebugAssembly3`.</span><span class="sxs-lookup"><span data-stu-id="84f40-103">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84f40-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="84f40-104">Syntax</span></span>  
  
```  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84f40-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="84f40-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="84f40-106">Um ponteiro para o endereço de um objeto ICorDebugAssembly que representa o assembly do contêiner, ou **nulo** se a chamada de método falhar.</span><span class="sxs-lookup"><span data-stu-id="84f40-106">A pointer to the address of an ICorDebugAssembly object that represents the container assembly, or **null** if the method call fails.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="84f40-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="84f40-107">Return Value</span></span>  
 <span data-ttu-id="84f40-108">`S_OK` Se a chamada do método for bem-sucedida; Caso contrário, `S_FALSE`, e `ppAssembly` é **nulo**.</span><span class="sxs-lookup"><span data-stu-id="84f40-108">`S_OK` if the method call succeeds; otherwise, `S_FALSE`, and `ppAssembly` is **null**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84f40-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="84f40-109">Remarks</span></span>  
 <span data-ttu-id="84f40-110">Se esse assembly foi mesclado com outros dentro de um assembly de contêiner único, esse método retorna o assembly do contêiner.</span><span class="sxs-lookup"><span data-stu-id="84f40-110">If this assembly has been merged with others inside a single container assembly, this method returns the container assembly.</span></span> <span data-ttu-id="84f40-111">Para obter mais informações e terminologia, consulte o [ICorDebugProcess6::EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="84f40-111">For more information and terminology, see the [ICorDebugProcess6::EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="84f40-112">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="84f40-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84f40-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="84f40-113">Requirements</span></span>  
 <span data-ttu-id="84f40-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84f40-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84f40-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="84f40-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84f40-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84f40-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84f40-117">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84f40-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84f40-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="84f40-118">See also</span></span>
- [<span data-ttu-id="84f40-119">Interface ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="84f40-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [<span data-ttu-id="84f40-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="84f40-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
