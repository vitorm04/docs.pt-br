---
title: Método ICorDebugDataTarget3::GetLoadedModules
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 120b839b2b11c85f42bb1a0ae4701de0dea33879
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912830"
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a><span data-ttu-id="25dfb-102">Método ICorDebugDataTarget3::GetLoadedModules</span><span class="sxs-lookup"><span data-stu-id="25dfb-102">ICorDebugDataTarget3::GetLoadedModules Method</span></span>
<span data-ttu-id="25dfb-103">Obtém uma lista dos módulos que foram carregados até agora.</span><span class="sxs-lookup"><span data-stu-id="25dfb-103">Gets a list of the modules that have been loaded so far.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25dfb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="25dfb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25dfb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="25dfb-105">Parameters</span></span>  
 `cRequestedModules`  
 <span data-ttu-id="25dfb-106">no O número de módulos para os quais as informações são solicitadas.</span><span class="sxs-lookup"><span data-stu-id="25dfb-106">[in] The number of modules for which information is requested.</span></span>  
  
 `pcFetchedModules`  
 <span data-ttu-id="25dfb-107">fora Um ponteiro para o número de módulos sobre os quais as informações foram retornadas.</span><span class="sxs-lookup"><span data-stu-id="25dfb-107">[out] A pointer to the number of modules about which information was returned.</span></span>  
  
 `pLoadedModules`  
 <span data-ttu-id="25dfb-108">fora Um ponteiro para uma matriz de objetos [ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md) que fornecem informações sobre os módulos carregados.</span><span class="sxs-lookup"><span data-stu-id="25dfb-108">[out] A pointer to an array of [ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md) objects that provide information about loaded modules.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25dfb-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="25dfb-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="25dfb-110">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="25dfb-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25dfb-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="25dfb-111">Requirements</span></span>  
 <span data-ttu-id="25dfb-112">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25dfb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25dfb-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="25dfb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25dfb-114">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25dfb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25dfb-115">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25dfb-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25dfb-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25dfb-116">See also</span></span>

- [<span data-ttu-id="25dfb-117">Interface ICorDebugDataTarget3</span><span class="sxs-lookup"><span data-stu-id="25dfb-117">ICorDebugDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)
- [<span data-ttu-id="25dfb-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="25dfb-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
