---
title: Método ICorDebugAssembly3::GetContainerAssembly
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9c01898bcbd76f7e6de9445d5d1f511203c100ed
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585179"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a><span data-ttu-id="ed1cf-102">Método ICorDebugAssembly3::GetContainerAssembly</span><span class="sxs-lookup"><span data-stu-id="ed1cf-102">ICorDebugAssembly3::GetContainerAssembly Method</span></span>
<span data-ttu-id="ed1cf-103">Retorna o assembly do contêiner desse objeto `ICorDebugAssembly3`.</span><span class="sxs-lookup"><span data-stu-id="ed1cf-103">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed1cf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ed1cf-104">Syntax</span></span>  
  
```  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ed1cf-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ed1cf-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="ed1cf-106">Um ponteiro para o endereço de um objeto ICorDebugAssembly que representa o assembly do contêiner, ou **nulo** se a chamada de método falhar.</span><span class="sxs-lookup"><span data-stu-id="ed1cf-106">A pointer to the address of an ICorDebugAssembly object that represents the container assembly, or **null** if the method call fails.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed1cf-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ed1cf-107">Return Value</span></span>  
 <span data-ttu-id="ed1cf-108">`S_OK` Se a chamada do método for bem-sucedida; Caso contrário, `S_FALSE`, e `ppAssembly` é **nulo**.</span><span class="sxs-lookup"><span data-stu-id="ed1cf-108">`S_OK` if the method call succeeds; otherwise, `S_FALSE`, and `ppAssembly` is **null**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed1cf-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="ed1cf-109">Remarks</span></span>  
 <span data-ttu-id="ed1cf-110">Se esse assembly foi mesclado com outros dentro de um assembly de contêiner único, esse método retorna o assembly do contêiner.</span><span class="sxs-lookup"><span data-stu-id="ed1cf-110">If this assembly has been merged with others inside a single container assembly, this method returns the container assembly.</span></span> <span data-ttu-id="ed1cf-111">Para obter mais informações e terminologia, consulte o [ICorDebugProcess6::EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="ed1cf-111">For more information and terminology, see the [ICorDebugProcess6::EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ed1cf-112">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ed1cf-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed1cf-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ed1cf-113">Requirements</span></span>  
 <span data-ttu-id="ed1cf-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed1cf-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed1cf-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ed1cf-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ed1cf-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ed1cf-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed1cf-117">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed1cf-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed1cf-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ed1cf-118">See also</span></span>
- [<span data-ttu-id="ed1cf-119">Interface ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="ed1cf-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [<span data-ttu-id="ed1cf-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="ed1cf-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
