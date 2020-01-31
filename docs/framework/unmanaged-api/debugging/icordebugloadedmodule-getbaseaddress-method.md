---
title: Método ICorDebugLoadedModule::GetBaseAddress
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
ms.openlocfilehash: 190c9114cffa537ba162b19abdf30d5a6aee87f8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788453"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="d038a-102">Método ICorDebugLoadedModule::GetBaseAddress</span><span class="sxs-lookup"><span data-stu-id="d038a-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="d038a-103">Obtém o endereço base do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="d038a-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d038a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d038a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d038a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d038a-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="d038a-106">fora Um ponteiro para o endereço base do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="d038a-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d038a-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="d038a-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d038a-108">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d038a-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d038a-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="d038a-109">Requirements</span></span>  
 <span data-ttu-id="d038a-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d038a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d038a-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d038a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d038a-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d038a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d038a-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d038a-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d038a-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="d038a-114">See also</span></span>

- [<span data-ttu-id="d038a-115">Interface ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="d038a-115">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="d038a-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="d038a-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
