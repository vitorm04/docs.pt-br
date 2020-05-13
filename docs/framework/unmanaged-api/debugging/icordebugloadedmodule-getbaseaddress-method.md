---
title: Método ICorDebugLoadedModule::GetBaseAddress
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
ms.openlocfilehash: d8c91c10577efd6a76af778cd01002de006df43a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209871"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="f6869-102">Método ICorDebugLoadedModule::GetBaseAddress</span><span class="sxs-lookup"><span data-stu-id="f6869-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="f6869-103">Obtém o endereço base do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="f6869-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6869-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f6869-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6869-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f6869-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="f6869-106">fora Um ponteiro para o endereço base do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="f6869-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6869-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="f6869-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6869-108">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f6869-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6869-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f6869-109">Requirements</span></span>  
 <span data-ttu-id="f6869-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6869-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6869-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f6869-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f6869-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6869-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6869-113">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6869-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6869-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="f6869-114">See also</span></span>

- [<span data-ttu-id="f6869-115">Interface ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="f6869-115">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="f6869-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="f6869-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
