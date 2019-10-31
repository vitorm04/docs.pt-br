---
title: Método ICorDebugDataTarget2::GetSymbolProviderForImage
ms.date: 03/30/2017
ms.assetid: b7c0a2f0-e904-43b3-98e1-d669e8a589e8
ms.openlocfilehash: 64a35f65bc3c31e091e2d94260efb84f20abb795
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122102"
---
# <a name="icordebugdatatarget2getsymbolproviderforimage-method"></a><span data-ttu-id="a75f5-102">Método ICorDebugDataTarget2::GetSymbolProviderForImage</span><span class="sxs-lookup"><span data-stu-id="a75f5-102">ICorDebugDataTarget2::GetSymbolProviderForImage Method</span></span>
<span data-ttu-id="a75f5-103">Retorna o provedor de símbolo para um módulo do endereço base do módulo.</span><span class="sxs-lookup"><span data-stu-id="a75f5-103">Returns the symbol-provider for a module from the base address of that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a75f5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a75f5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolProviderForImage(  
    [in] CORDB_ADDRESS imageBaseAddress,   
    [out] ICorDebugSymbolProvider **ppSymProvider  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a75f5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a75f5-105">Parameters</span></span>  
 `imageBaseAddress`  
 <span data-ttu-id="a75f5-106">no Um valor [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) que representa o endereço base de um módulo.</span><span class="sxs-lookup"><span data-stu-id="a75f5-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the base address of a module.</span></span>  
  
 `ppSymProvider`  
 <span data-ttu-id="a75f5-107">fora Um ponteiro para o endereço de um objeto [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a75f5-107">[out] A pointer to the address of an [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a75f5-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="a75f5-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a75f5-109">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a75f5-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a75f5-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a75f5-110">Requirements</span></span>  
 <span data-ttu-id="a75f5-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a75f5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a75f5-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a75f5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a75f5-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a75f5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a75f5-114">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a75f5-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a75f5-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a75f5-115">See also</span></span>

- [<span data-ttu-id="a75f5-116">Interface ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="a75f5-116">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="a75f5-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a75f5-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
