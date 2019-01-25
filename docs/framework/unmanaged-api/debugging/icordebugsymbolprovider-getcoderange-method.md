---
title: Método ICorDebugSymbolProvider::GetCodeRange
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bfaa8ce16a3874d28e06bdb77f1e903548c0a03b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684782"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="8645a-102">Método ICorDebugSymbolProvider::GetCodeRange</span><span class="sxs-lookup"><span data-stu-id="8645a-102">ICorDebugSymbolProvider::GetCodeRange Method</span></span>
<span data-ttu-id="8645a-103">Obtém o endereço de início do método e o tamanho fornecido um endereço virtual relativo (RVA) em um método.</span><span class="sxs-lookup"><span data-stu-id="8645a-103">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8645a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8645a-104">Syntax</span></span>  
  
```  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,   
   [out] ULONG32* pCodeStartAddress,   
   [out] ULONG32* pCodeSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8645a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8645a-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="8645a-106">[in] O endereço virtual relativo (RVA) em um método.</span><span class="sxs-lookup"><span data-stu-id="8645a-106">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="8645a-107">[out] Um ponteiro para o endereço inicial do método.</span><span class="sxs-lookup"><span data-stu-id="8645a-107">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="8645a-108">Um ponteiro para o tamanho do código do método (o número de bytes de código do método).</span><span class="sxs-lookup"><span data-stu-id="8645a-108">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8645a-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="8645a-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8645a-110">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8645a-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8645a-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8645a-111">Requirements</span></span>  
 <span data-ttu-id="8645a-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8645a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8645a-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8645a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8645a-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8645a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8645a-115">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8645a-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8645a-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8645a-116">See also</span></span>
- [<span data-ttu-id="8645a-117">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="8645a-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="8645a-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="8645a-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
