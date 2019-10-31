---
title: Método ICorDebugAssembly3::EnumerateContainedAssemblies
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
ms.openlocfilehash: 032f32a08efa92cea682b0e2fc974dc607a9dca4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133945"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a><span data-ttu-id="40bbd-102">Método ICorDebugAssembly3::EnumerateContainedAssemblies</span><span class="sxs-lookup"><span data-stu-id="40bbd-102">ICorDebugAssembly3::EnumerateContainedAssemblies Method</span></span>
<span data-ttu-id="40bbd-103">Obtém um enumerador para os assemblies contidos neste assembly.</span><span class="sxs-lookup"><span data-stu-id="40bbd-103">Gets an enumerator for the assemblies contained in this assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40bbd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="40bbd-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40bbd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="40bbd-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="40bbd-106">fora Um ponteiro para o endereço de um objeto de interface ICorDebugAssemblyEnum que é o enumerador.</span><span class="sxs-lookup"><span data-stu-id="40bbd-106">[out] A pointer to the address of an ICorDebugAssemblyEnum interface object that is the enumerator.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="40bbd-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="40bbd-107">Return Value</span></span>  
 <span data-ttu-id="40bbd-108">`S_OK` Se este objeto `ICorDebugAssembly3` for um contêiner; caso contrário, `S_FALSE`, e a enumeração está vazia.</span><span class="sxs-lookup"><span data-stu-id="40bbd-108">`S_OK` if this `ICorDebugAssembly3` object is a container; otherwise, `S_FALSE`, and the enumeration is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40bbd-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="40bbd-109">Remarks</span></span>  
 <span data-ttu-id="40bbd-110">Símbolos são necessários para enumerar os assemblies contidos.</span><span class="sxs-lookup"><span data-stu-id="40bbd-110">Symbols are needed to enumerate the contained assemblies.</span></span> <span data-ttu-id="40bbd-111">Se eles não estiverem presentes, o método retorna `S_FALSE`, e nenhum enumerador válido é fornecido.</span><span class="sxs-lookup"><span data-stu-id="40bbd-111">If they aren't present, the method returns `S_FALSE`, and no valid enumerator is provided.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40bbd-112">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="40bbd-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40bbd-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="40bbd-113">Requirements</span></span>  
 <span data-ttu-id="40bbd-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40bbd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40bbd-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="40bbd-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="40bbd-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="40bbd-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40bbd-117">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40bbd-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40bbd-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="40bbd-118">See also</span></span>

- [<span data-ttu-id="40bbd-119">Interface ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="40bbd-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [<span data-ttu-id="40bbd-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="40bbd-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
