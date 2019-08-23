---
title: 'Método ICorDebugStaticFieldSymbol:: GetAddress'
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d41b99d7410333cb6a22443271c1fcbc41c3594
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962707"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="96c4c-102">Método ICorDebugStaticFieldSymbol:: GetAddress</span><span class="sxs-lookup"><span data-stu-id="96c4c-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>
<span data-ttu-id="96c4c-103">Obtém o endereço de um campo estático.</span><span class="sxs-lookup"><span data-stu-id="96c4c-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96c4c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="96c4c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96c4c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="96c4c-105">Parameters</span></span>  
 <span data-ttu-id="96c4c-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="96c4c-106">pRVA</span></span>  
 <span data-ttu-id="96c4c-107">fora Um ponteiro para o endereço virtual relativo (RVA) do campo estático.</span><span class="sxs-lookup"><span data-stu-id="96c4c-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96c4c-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="96c4c-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="96c4c-109">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="96c4c-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96c4c-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="96c4c-110">Requirements</span></span>  
 <span data-ttu-id="96c4c-111">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96c4c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96c4c-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="96c4c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96c4c-113">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96c4c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96c4c-114">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96c4c-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96c4c-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96c4c-115">See also</span></span>

- [<span data-ttu-id="96c4c-116">Interface ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="96c4c-116">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="96c4c-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="96c4c-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
