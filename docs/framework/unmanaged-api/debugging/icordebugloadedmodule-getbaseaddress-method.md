---
title: Método ICorDebugLoadedModule::GetBaseAddress
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e84d6deca0cd09cc547636007208c70ab91c1ab1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223531"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="88e84-102">Método ICorDebugLoadedModule::GetBaseAddress</span><span class="sxs-lookup"><span data-stu-id="88e84-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="88e84-103">Obtém o endereço base do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="88e84-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88e84-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="88e84-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88e84-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="88e84-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="88e84-106">[out] Um ponteiro para o endereço base do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="88e84-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88e84-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="88e84-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88e84-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="88e84-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88e84-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="88e84-109">Requirements</span></span>  
 <span data-ttu-id="88e84-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88e84-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88e84-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="88e84-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="88e84-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88e84-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88e84-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88e84-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88e84-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88e84-114">See also</span></span>

- [<span data-ttu-id="88e84-115">Interface ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="88e84-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="88e84-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="88e84-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
