---
title: Método ICorDebugAssembly3::GetContainerAssembly
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9bd4cd44eca9b12ab8773fd75b6262579cfe8e8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206077"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a><span data-ttu-id="585f8-102">Método ICorDebugAssembly3::GetContainerAssembly</span><span class="sxs-lookup"><span data-stu-id="585f8-102">ICorDebugAssembly3::GetContainerAssembly Method</span></span>
<span data-ttu-id="585f8-103">Retorna o assembly do contêiner desse objeto `ICorDebugAssembly3`.</span><span class="sxs-lookup"><span data-stu-id="585f8-103">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="585f8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="585f8-104">Syntax</span></span>  
  
```  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="585f8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="585f8-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="585f8-106">Um ponteiro para o endereço de um objeto ICorDebugAssembly que representa o assembly do contêiner, ou **nulo** se a chamada de método falhar.</span><span class="sxs-lookup"><span data-stu-id="585f8-106">A pointer to the address of an ICorDebugAssembly object that represents the container assembly, or **null** if the method call fails.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="585f8-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="585f8-107">Return Value</span></span>  
 `S_OK` <span data-ttu-id="585f8-108">Se a chamada do método for bem-sucedida; Caso contrário, `S_FALSE`, e `ppAssembly` é **nulo**.</span><span class="sxs-lookup"><span data-stu-id="585f8-108">if the method call succeeds; otherwise, `S_FALSE`, and `ppAssembly` is **null**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="585f8-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="585f8-109">Remarks</span></span>  
 <span data-ttu-id="585f8-110">Se esse assembly foi mesclado com outros dentro de um assembly de contêiner único, esse método retorna o assembly do contêiner.</span><span class="sxs-lookup"><span data-stu-id="585f8-110">If this assembly has been merged with others inside a single container assembly, this method returns the container assembly.</span></span> <span data-ttu-id="585f8-111">Para obter mais informações e terminologia, consulte o [ICorDebugProcess6::EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="585f8-111">For more information and terminology, see the [ICorDebugProcess6::EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="585f8-112">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="585f8-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="585f8-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="585f8-113">Requirements</span></span>  
 <span data-ttu-id="585f8-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="585f8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="585f8-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="585f8-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="585f8-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="585f8-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="585f8-117">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="585f8-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="585f8-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="585f8-118">See also</span></span>

- [<span data-ttu-id="585f8-119">Interface ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="585f8-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [<span data-ttu-id="585f8-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="585f8-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
