---
title: 'Método ICorDebugStaticFieldSymbol:: GetAddress'
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
ms.openlocfilehash: 65761e48491b2a4c81ccd05b17d8723f71f52e5c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131794"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="1b295-102">Método ICorDebugStaticFieldSymbol:: GetAddress</span><span class="sxs-lookup"><span data-stu-id="1b295-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>
<span data-ttu-id="1b295-103">Obtém o endereço de um campo estático.</span><span class="sxs-lookup"><span data-stu-id="1b295-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b295-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1b295-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b295-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1b295-105">Parameters</span></span>  
 <span data-ttu-id="1b295-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="1b295-106">pRVA</span></span>  
 <span data-ttu-id="1b295-107">fora Um ponteiro para o endereço virtual relativo (RVA) do campo estático.</span><span class="sxs-lookup"><span data-stu-id="1b295-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b295-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="1b295-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1b295-109">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1b295-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b295-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1b295-110">Requirements</span></span>  
 <span data-ttu-id="1b295-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b295-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b295-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b295-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b295-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b295-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b295-114">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b295-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b295-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1b295-115">See also</span></span>

- [<span data-ttu-id="1b295-116">Interface ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="1b295-116">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="1b295-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="1b295-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
