---
title: Método ICorDebugStaticFieldSymbol::GetAddress
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e233fe78f6b2c721114f0307a8ca414625a0087e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59160414"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="a3f02-102">Método ICorDebugStaticFieldSymbol::GetAddress</span><span class="sxs-lookup"><span data-stu-id="a3f02-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>
<span data-ttu-id="a3f02-103">Obtém o endereço de um campo estático.</span><span class="sxs-lookup"><span data-stu-id="a3f02-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3f02-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a3f02-104">Syntax</span></span>  
  
```  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3f02-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a3f02-105">Parameters</span></span>  
 <span data-ttu-id="a3f02-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="a3f02-106">pRVA</span></span>  
 <span data-ttu-id="a3f02-107">[out] Um ponteiro para o endereço virtual relativo (RVA) do campo estático.</span><span class="sxs-lookup"><span data-stu-id="a3f02-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3f02-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="a3f02-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3f02-109">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a3f02-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3f02-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a3f02-110">Requirements</span></span>  
 <span data-ttu-id="a3f02-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3f02-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3f02-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a3f02-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a3f02-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3f02-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3f02-114">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3f02-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3f02-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a3f02-115">See also</span></span>

- [<span data-ttu-id="a3f02-116">Interface ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="a3f02-116">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="a3f02-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a3f02-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
