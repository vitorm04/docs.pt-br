---
title: Método ICorDebugLoadedModule::GetSize
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
ms.openlocfilehash: f207cd1c612b6444a9512adaa356ac2d01de7b9f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788461"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="03d60-102">Método ICorDebugLoadedModule::GetSize</span><span class="sxs-lookup"><span data-stu-id="03d60-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="03d60-103">Obtém o tamanho em bytes do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="03d60-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03d60-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="03d60-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03d60-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="03d60-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="03d60-106">fora Um ponteiro para o número de bytes no módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="03d60-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03d60-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="03d60-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="03d60-108">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="03d60-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03d60-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="03d60-109">Requirements</span></span>  
 <span data-ttu-id="03d60-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03d60-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03d60-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="03d60-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="03d60-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="03d60-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03d60-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03d60-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03d60-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="03d60-114">See also</span></span>

- [<span data-ttu-id="03d60-115">Interface ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="03d60-115">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="03d60-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="03d60-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
