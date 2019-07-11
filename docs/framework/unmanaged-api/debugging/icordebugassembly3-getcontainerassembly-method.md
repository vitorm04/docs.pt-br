---
title: Método ICorDebugAssembly3::GetContainerAssembly
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dbe28c01891464ff45dfec97b1d8b4685ba8a51a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744370"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a><span data-ttu-id="4dcc5-102">Método ICorDebugAssembly3::GetContainerAssembly</span><span class="sxs-lookup"><span data-stu-id="4dcc5-102">ICorDebugAssembly3::GetContainerAssembly Method</span></span>
<span data-ttu-id="4dcc5-103">Retorna o assembly do contêiner desse objeto `ICorDebugAssembly3`.</span><span class="sxs-lookup"><span data-stu-id="4dcc5-103">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dcc5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4dcc5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4dcc5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4dcc5-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="4dcc5-106">Um ponteiro para o endereço de um objeto ICorDebugAssembly que representa o assembly do contêiner, ou **nulo** se a chamada de método falhar.</span><span class="sxs-lookup"><span data-stu-id="4dcc5-106">A pointer to the address of an ICorDebugAssembly object that represents the container assembly, or **null** if the method call fails.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4dcc5-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4dcc5-107">Return Value</span></span>  
 <span data-ttu-id="4dcc5-108">`S_OK` Se a chamada do método for bem-sucedida; Caso contrário, `S_FALSE`, e `ppAssembly` é **nulo**.</span><span class="sxs-lookup"><span data-stu-id="4dcc5-108">`S_OK` if the method call succeeds; otherwise, `S_FALSE`, and `ppAssembly` is **null**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4dcc5-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="4dcc5-109">Remarks</span></span>  
 <span data-ttu-id="4dcc5-110">Se esse assembly foi mesclado com outros dentro de um assembly de contêiner único, esse método retorna o assembly do contêiner.</span><span class="sxs-lookup"><span data-stu-id="4dcc5-110">If this assembly has been merged with others inside a single container assembly, this method returns the container assembly.</span></span> <span data-ttu-id="4dcc5-111">Para obter mais informações e terminologia, consulte o [ICorDebugProcess6::EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="4dcc5-111">For more information and terminology, see the [ICorDebugProcess6::EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4dcc5-112">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4dcc5-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4dcc5-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4dcc5-113">Requirements</span></span>  
 <span data-ttu-id="4dcc5-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4dcc5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4dcc5-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4dcc5-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4dcc5-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4dcc5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4dcc5-117">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4dcc5-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dcc5-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4dcc5-118">See also</span></span>

- [<span data-ttu-id="4dcc5-119">Interface ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="4dcc5-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [<span data-ttu-id="4dcc5-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="4dcc5-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
