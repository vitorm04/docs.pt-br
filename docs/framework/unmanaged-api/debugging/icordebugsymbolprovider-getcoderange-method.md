---
title: Método ICorDebugSymbolProvider::GetCodeRange
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f60ba1c68e95363a59c5a1d217756664f63e5256
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420118"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="3bf65-102">Método ICorDebugSymbolProvider::GetCodeRange</span><span class="sxs-lookup"><span data-stu-id="3bf65-102">ICorDebugSymbolProvider::GetCodeRange Method</span></span>
<span data-ttu-id="3bf65-103">Obtém o endereço de início do método e o tamanho fornecido um endereço virtual relativo (RVA) em um método.</span><span class="sxs-lookup"><span data-stu-id="3bf65-103">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bf65-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3bf65-104">Syntax</span></span>  
  
```  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,   
   [out] ULONG32* pCodeStartAddress,   
   [out] ULONG32* pCodeSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3bf65-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3bf65-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="3bf65-106">[in] O virtual endereço relativo (RVA) em um método.</span><span class="sxs-lookup"><span data-stu-id="3bf65-106">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="3bf65-107">[out] Um ponteiro para o endereço inicial do método.</span><span class="sxs-lookup"><span data-stu-id="3bf65-107">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="3bf65-108">Um ponteiro para o tamanho de código do método (o número de bytes de código do método).</span><span class="sxs-lookup"><span data-stu-id="3bf65-108">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3bf65-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="3bf65-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3bf65-110">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3bf65-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bf65-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3bf65-111">Requirements</span></span>  
 <span data-ttu-id="3bf65-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bf65-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bf65-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3bf65-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3bf65-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3bf65-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3bf65-115">**Versões do .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bf65-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bf65-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3bf65-116">See Also</span></span>  
 [<span data-ttu-id="3bf65-117">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="3bf65-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="3bf65-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="3bf65-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
