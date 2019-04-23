---
title: Método ICorDebugAssembly3::EnumerateContainedAssemblies
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54ccb52468a530280527252e0e0c43cc9edbb2c3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080950"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a><span data-ttu-id="158ca-102">Método ICorDebugAssembly3::EnumerateContainedAssemblies</span><span class="sxs-lookup"><span data-stu-id="158ca-102">ICorDebugAssembly3::EnumerateContainedAssemblies Method</span></span>
<span data-ttu-id="158ca-103">Obtém um enumerador para os assemblies contidos neste assembly.</span><span class="sxs-lookup"><span data-stu-id="158ca-103">Gets an enumerator for the assemblies contained in this assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="158ca-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="158ca-104">Syntax</span></span>  
  
```  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="158ca-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="158ca-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="158ca-106">[out] Um ponteiro para o endereço de um objeto de interface ICorDebugAssemblyEnum que é o enumerador.</span><span class="sxs-lookup"><span data-stu-id="158ca-106">[out] A pointer to the address of an ICorDebugAssemblyEnum interface object that is the enumerator.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="158ca-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="158ca-107">Return Value</span></span>  
 <span data-ttu-id="158ca-108">`S_OK` Se este objeto `ICorDebugAssembly3` for um contêiner; caso contrário, `S_FALSE`, e a enumeração está vazia.</span><span class="sxs-lookup"><span data-stu-id="158ca-108">`S_OK` if this `ICorDebugAssembly3` object is a container; otherwise, `S_FALSE`, and the enumeration is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="158ca-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="158ca-109">Remarks</span></span>  
 <span data-ttu-id="158ca-110">Símbolos são necessários para enumerar os assemblies contidos.</span><span class="sxs-lookup"><span data-stu-id="158ca-110">Symbols are needed to enumerate the contained assemblies.</span></span> <span data-ttu-id="158ca-111">Se eles não estiverem presentes, o método retorna `S_FALSE`, e nenhum enumerador válido é fornecido.</span><span class="sxs-lookup"><span data-stu-id="158ca-111">If they aren't present, the method returns `S_FALSE`, and no valid enumerator is provided.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="158ca-112">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="158ca-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="158ca-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="158ca-113">Requirements</span></span>  
 <span data-ttu-id="158ca-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="158ca-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="158ca-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="158ca-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="158ca-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="158ca-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="158ca-117">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="158ca-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="158ca-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="158ca-118">See also</span></span>

- [<span data-ttu-id="158ca-119">Interface ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="158ca-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [<span data-ttu-id="158ca-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="158ca-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
