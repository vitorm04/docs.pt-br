---
title: 'Método ICorDebugStaticFieldSymbol:: GetSize'
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
ms.openlocfilehash: deeb887dad38417e3ebb980f5ef2f89392388d65
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791814"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="9af11-102">Método ICorDebugStaticFieldSymbol:: GetSize</span><span class="sxs-lookup"><span data-stu-id="9af11-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="9af11-103">Obtém o tamanho em bytes do campo estático.</span><span class="sxs-lookup"><span data-stu-id="9af11-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9af11-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9af11-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9af11-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9af11-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="9af11-106">fora Um ponteiro para o comprimento do campo.</span><span class="sxs-lookup"><span data-stu-id="9af11-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9af11-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="9af11-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9af11-108">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9af11-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9af11-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="9af11-109">Requirements</span></span>  
 <span data-ttu-id="9af11-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9af11-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9af11-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9af11-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9af11-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9af11-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9af11-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9af11-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9af11-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="9af11-114">See also</span></span>

- [<span data-ttu-id="9af11-115">Interface ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="9af11-115">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="9af11-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="9af11-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
