---
title: Método ICorDebugLoadedModule::GetBaseAddress
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c12ea84f1a706850972b2e404ec52eea3523de7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412630"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="91ca7-102">Método ICorDebugLoadedModule::GetBaseAddress</span><span class="sxs-lookup"><span data-stu-id="91ca7-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="91ca7-103">Obtém o endereço base do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="91ca7-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91ca7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="91ca7-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="91ca7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="91ca7-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="91ca7-106">[out] Um ponteiro para o endereço base do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="91ca7-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91ca7-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="91ca7-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="91ca7-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="91ca7-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91ca7-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="91ca7-109">Requirements</span></span>  
 <span data-ttu-id="91ca7-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91ca7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91ca7-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="91ca7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91ca7-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91ca7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91ca7-113">**Versões do .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91ca7-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91ca7-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91ca7-114">See Also</span></span>  
 [<span data-ttu-id="91ca7-115">Interface ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="91ca7-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="91ca7-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="91ca7-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
