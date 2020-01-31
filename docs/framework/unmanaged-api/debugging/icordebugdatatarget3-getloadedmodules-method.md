---
title: Método ICorDebugDataTarget3::GetLoadedModules
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
ms.openlocfilehash: d4c22146422085daa4dc9d90ae5b3735a12500c2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793563"
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a><span data-ttu-id="49478-102">Método ICorDebugDataTarget3::GetLoadedModules</span><span class="sxs-lookup"><span data-stu-id="49478-102">ICorDebugDataTarget3::GetLoadedModules Method</span></span>
<span data-ttu-id="49478-103">Obtém uma lista dos módulos que foram carregados até agora.</span><span class="sxs-lookup"><span data-stu-id="49478-103">Gets a list of the modules that have been loaded so far.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49478-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="49478-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49478-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="49478-105">Parameters</span></span>  
 `cRequestedModules`  
 <span data-ttu-id="49478-106">no O número de módulos para os quais as informações são solicitadas.</span><span class="sxs-lookup"><span data-stu-id="49478-106">[in] The number of modules for which information is requested.</span></span>  
  
 `pcFetchedModules`  
 <span data-ttu-id="49478-107">fora Um ponteiro para o número de módulos sobre os quais as informações foram retornadas.</span><span class="sxs-lookup"><span data-stu-id="49478-107">[out] A pointer to the number of modules about which information was returned.</span></span>  
  
 `pLoadedModules`  
 <span data-ttu-id="49478-108">fora Um ponteiro para uma matriz de objetos [ICorDebugLoadedModule](icordebugloadedmodule-interface.md) que fornecem informações sobre os módulos carregados.</span><span class="sxs-lookup"><span data-stu-id="49478-108">[out] A pointer to an array of [ICorDebugLoadedModule](icordebugloadedmodule-interface.md) objects that provide information about loaded modules.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49478-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="49478-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="49478-110">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="49478-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49478-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="49478-111">Requirements</span></span>  
 <span data-ttu-id="49478-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49478-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49478-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="49478-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49478-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49478-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49478-115">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49478-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49478-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="49478-116">See also</span></span>

- [<span data-ttu-id="49478-117">Interface ICorDebugDataTarget3</span><span class="sxs-lookup"><span data-stu-id="49478-117">ICorDebugDataTarget3 Interface</span></span>](icordebugdatatarget3-interface.md)
- [<span data-ttu-id="49478-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="49478-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
