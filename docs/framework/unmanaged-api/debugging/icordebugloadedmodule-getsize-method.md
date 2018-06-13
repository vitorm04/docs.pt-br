---
title: Método ICorDebugLoadedModule::GetSize
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9768fb91749158bf3193919b2106bde1c618468a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413225"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="41178-102">Método ICorDebugLoadedModule::GetSize</span><span class="sxs-lookup"><span data-stu-id="41178-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="41178-103">Obtém o tamanho em bytes do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="41178-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41178-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="41178-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="41178-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41178-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="41178-106">[out] Um ponteiro para o número de bytes no módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="41178-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41178-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="41178-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41178-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="41178-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41178-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="41178-109">Requirements</span></span>  
 <span data-ttu-id="41178-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41178-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41178-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="41178-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41178-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41178-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41178-113">**Versões do .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41178-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41178-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41178-114">See Also</span></span>  
 [<span data-ttu-id="41178-115">Interface ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="41178-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="41178-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="41178-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
