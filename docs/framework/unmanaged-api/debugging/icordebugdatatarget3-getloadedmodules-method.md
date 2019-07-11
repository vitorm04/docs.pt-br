---
title: Método ICorDebugDataTarget3::GetLoadedModules
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fc62618c5872a2c3e3740be4c60ae02e386c1868
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750035"
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a><span data-ttu-id="61e3f-102">Método ICorDebugDataTarget3::GetLoadedModules</span><span class="sxs-lookup"><span data-stu-id="61e3f-102">ICorDebugDataTarget3::GetLoadedModules Method</span></span>
<span data-ttu-id="61e3f-103">Obtém uma lista dos módulos que foram carregados até o momento.</span><span class="sxs-lookup"><span data-stu-id="61e3f-103">Gets a list of the modules that have been loaded so far.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61e3f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="61e3f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61e3f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="61e3f-105">Parameters</span></span>  
 `cRequestedModules`  
 <span data-ttu-id="61e3f-106">[in] O número de módulos para o qual as informações são solicitadas.</span><span class="sxs-lookup"><span data-stu-id="61e3f-106">[in] The number of modules for which information is requested.</span></span>  
  
 `pcFetchedModules`  
 <span data-ttu-id="61e3f-107">[out] Um ponteiro para o número de módulos sobre qual informação foi retornada.</span><span class="sxs-lookup"><span data-stu-id="61e3f-107">[out] A pointer to the number of modules about which information was returned.</span></span>  
  
 `pLoadedModules`  
 <span data-ttu-id="61e3f-108">[out] Um ponteiro para uma matriz de [ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md) objetos que fornecem informações sobre os módulos carregados.</span><span class="sxs-lookup"><span data-stu-id="61e3f-108">[out] A pointer to an array of [ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md) objects that provide information about loaded modules.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61e3f-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="61e3f-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="61e3f-110">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="61e3f-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61e3f-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="61e3f-111">Requirements</span></span>  
 <span data-ttu-id="61e3f-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61e3f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61e3f-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="61e3f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61e3f-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61e3f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61e3f-115">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61e3f-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61e3f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61e3f-116">See also</span></span>

- [<span data-ttu-id="61e3f-117">Interface ICorDebugDataTarget3</span><span class="sxs-lookup"><span data-stu-id="61e3f-117">ICorDebugDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)
- [<span data-ttu-id="61e3f-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="61e3f-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
