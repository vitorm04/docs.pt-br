---
title: Método ICorDebugLoadedModule::GetSize
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
ms.openlocfilehash: 6a1c8c94b3c45ac995501b84bb4a69d73e7db25b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209845"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="b7f30-102">Método ICorDebugLoadedModule::GetSize</span><span class="sxs-lookup"><span data-stu-id="b7f30-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="b7f30-103">Obtém o tamanho em bytes do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="b7f30-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7f30-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7f30-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7f30-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b7f30-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="b7f30-106">fora Um ponteiro para o número de bytes no módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="b7f30-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7f30-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="b7f30-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b7f30-108">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b7f30-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7f30-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b7f30-109">Requirements</span></span>  
 <span data-ttu-id="b7f30-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7f30-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7f30-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7f30-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7f30-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7f30-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7f30-113">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7f30-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7f30-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="b7f30-114">See also</span></span>

- [<span data-ttu-id="b7f30-115">Interface ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="b7f30-115">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="b7f30-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="b7f30-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
