---
title: Método ICorDebugSymbolProvider::GetCodeRange
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 392f526df53474dd2926e631e24ec5449bd1b199
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498465"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="c05da-102">Método ICorDebugSymbolProvider::GetCodeRange</span><span class="sxs-lookup"><span data-stu-id="c05da-102">ICorDebugSymbolProvider::GetCodeRange Method</span></span>
<span data-ttu-id="c05da-103">Obtém o endereço de início do método e o tamanho fornecido um endereço virtual relativo (RVA) em um método.</span><span class="sxs-lookup"><span data-stu-id="c05da-103">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c05da-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c05da-104">Syntax</span></span>  
  
```  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,   
   [out] ULONG32* pCodeStartAddress,   
   [out] ULONG32* pCodeSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c05da-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c05da-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="c05da-106">[in] O endereço virtual relativo (RVA) em um método.</span><span class="sxs-lookup"><span data-stu-id="c05da-106">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="c05da-107">[out] Um ponteiro para o endereço inicial do método.</span><span class="sxs-lookup"><span data-stu-id="c05da-107">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="c05da-108">Um ponteiro para o tamanho do código do método (o número de bytes de código do método).</span><span class="sxs-lookup"><span data-stu-id="c05da-108">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c05da-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="c05da-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c05da-110">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c05da-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c05da-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c05da-111">Requirements</span></span>  
 <span data-ttu-id="c05da-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c05da-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c05da-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c05da-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c05da-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c05da-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c05da-115">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c05da-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c05da-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c05da-116">See also</span></span>
- [<span data-ttu-id="c05da-117">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="c05da-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="c05da-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="c05da-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
