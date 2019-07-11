---
title: Método ICorDebugLoadedModule::GetBaseAddress
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: adb01b8aa57bf3ed928578d15e0859b9ac73bc7d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759928"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="f9f19-102">Método ICorDebugLoadedModule::GetBaseAddress</span><span class="sxs-lookup"><span data-stu-id="f9f19-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="f9f19-103">Obtém o endereço base do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="f9f19-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9f19-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f9f19-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9f19-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f9f19-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="f9f19-106">[out] Um ponteiro para o endereço base do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="f9f19-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9f19-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="f9f19-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f9f19-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f9f19-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9f19-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f9f19-109">Requirements</span></span>  
 <span data-ttu-id="f9f19-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9f19-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9f19-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f9f19-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9f19-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9f19-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9f19-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9f19-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9f19-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9f19-114">See also</span></span>

- [<span data-ttu-id="f9f19-115">Interface ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="f9f19-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="f9f19-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="f9f19-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
