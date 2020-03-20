---
title: ICorDebugSymbolProvider::GetCodeRange Method
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
ms.openlocfilehash: 81babade2ba499ce9326c664e83fa582abbd216f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178477"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="b8022-102">ICorDebugSymbolProvider::GetCodeRange Method</span><span class="sxs-lookup"><span data-stu-id="b8022-102">ICorDebugSymbolProvider::GetCodeRange Method</span></span>
<span data-ttu-id="b8022-103">Obtém o endereço inicial e o tamanho do método, dado um endereço virtual relativo (RVA) em um método.</span><span class="sxs-lookup"><span data-stu-id="b8022-103">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8022-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8022-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,
   [out] ULONG32* pCodeStartAddress,
   [out] ULONG32* pCodeSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8022-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="b8022-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="b8022-106">[em] O endereço virtual relativo (RVA) em um método.</span><span class="sxs-lookup"><span data-stu-id="b8022-106">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="b8022-107">[fora] Um ponteiro para o endereço inicial do método.</span><span class="sxs-lookup"><span data-stu-id="b8022-107">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="b8022-108">Um ponteiro para o tamanho do código do método (o número de bytes do código do método).</span><span class="sxs-lookup"><span data-stu-id="b8022-108">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8022-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="b8022-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b8022-110">Este método está disponível apenas com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b8022-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8022-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b8022-111">Requirements</span></span>  
 <span data-ttu-id="b8022-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8022-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8022-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8022-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8022-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8022-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8022-115">**.NET Framework Versions:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8022-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8022-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="b8022-116">See also</span></span>

- [<span data-ttu-id="b8022-117">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="b8022-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="b8022-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="b8022-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
