---
title: 'Método ICorDebugSymbolProvider2:: GetFrameProps'
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c22e9c58a203c13611298e1956a6951d8ca7e8b6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955507"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="c6b4c-102">Método ICorDebugSymbolProvider2:: GetFrameProps</span><span class="sxs-lookup"><span data-stu-id="c6b4c-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>
<span data-ttu-id="c6b4c-103">Retorna o método iniciando o endereço virtual relativo de um método e o quadro pai, dado um endereço virtual relativo de código.</span><span class="sxs-lookup"><span data-stu-id="c6b4c-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6b4c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c6b4c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6b4c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c6b4c-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="c6b4c-106">no Um endereço virtual relativo ao código.</span><span class="sxs-lookup"><span data-stu-id="c6b4c-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="c6b4c-107">fora Um ponteiro para o endereço virtual relativo inicial do método.</span><span class="sxs-lookup"><span data-stu-id="c6b4c-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="c6b4c-108">fora Um ponteiro para o endereço virtual relativo inicial do quadro.</span><span class="sxs-lookup"><span data-stu-id="c6b4c-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6b4c-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="c6b4c-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c6b4c-110">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c6b4c-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6b4c-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c6b4c-111">Requirements</span></span>  
 <span data-ttu-id="c6b4c-112">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6b4c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6b4c-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c6b4c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6b4c-114">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6b4c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6b4c-115">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6b4c-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6b4c-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6b4c-116">See also</span></span>

- [<span data-ttu-id="c6b4c-117">Interface ICorDebugSymbolProvider2</span><span class="sxs-lookup"><span data-stu-id="c6b4c-117">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="c6b4c-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="c6b4c-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
