---
title: Método ICorDebugLoadedModule::GetSize
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4c4888419bb13db43a4a15d98965cc8d3cb8e77
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54515569"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="1b5cc-102">Método ICorDebugLoadedModule::GetSize</span><span class="sxs-lookup"><span data-stu-id="1b5cc-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="1b5cc-103">Obtém o tamanho em bytes do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="1b5cc-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b5cc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1b5cc-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1b5cc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1b5cc-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="1b5cc-106">[out] Um ponteiro para o número de bytes no módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="1b5cc-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b5cc-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="1b5cc-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b5cc-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1b5cc-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b5cc-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1b5cc-109">Requirements</span></span>  
 <span data-ttu-id="1b5cc-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b5cc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b5cc-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b5cc-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b5cc-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b5cc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b5cc-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b5cc-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b5cc-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1b5cc-114">See also</span></span>
- [<span data-ttu-id="1b5cc-115">Interface ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="1b5cc-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="1b5cc-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="1b5cc-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
