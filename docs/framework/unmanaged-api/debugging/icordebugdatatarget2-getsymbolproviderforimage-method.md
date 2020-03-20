---
title: Método ICorDebugDataTarget2::GetSymbolProviderForImage
ms.date: 03/30/2017
ms.assetid: b7c0a2f0-e904-43b3-98e1-d669e8a589e8
ms.openlocfilehash: 500d36b414be686071990a6e1b40dd8759d02ae9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178928"
---
# <a name="icordebugdatatarget2getsymbolproviderforimage-method"></a><span data-ttu-id="92518-102">Método ICorDebugDataTarget2::GetSymbolProviderForImage</span><span class="sxs-lookup"><span data-stu-id="92518-102">ICorDebugDataTarget2::GetSymbolProviderForImage Method</span></span>
<span data-ttu-id="92518-103">Retorna o provedor de símbolo para um módulo do endereço base do módulo.</span><span class="sxs-lookup"><span data-stu-id="92518-103">Returns the symbol-provider for a module from the base address of that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92518-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="92518-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolProviderForImage(  
    [in] CORDB_ADDRESS imageBaseAddress,
    [out] ICorDebugSymbolProvider **ppSymProvider  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92518-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="92518-105">Parameters</span></span>  
 `imageBaseAddress`  
 <span data-ttu-id="92518-106">[em] Um [valor CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) que representa o endereço base de um módulo.</span><span class="sxs-lookup"><span data-stu-id="92518-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the base address of a module.</span></span>  
  
 `ppSymProvider`  
 <span data-ttu-id="92518-107">[fora] Um ponteiro para o endereço de um objeto [ICorDebugSymbolProvider.](icordebugsymbolprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="92518-107">[out] A pointer to the address of an [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92518-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="92518-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="92518-109">Este método está disponível apenas com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="92518-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92518-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="92518-110">Requirements</span></span>  
 <span data-ttu-id="92518-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92518-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92518-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="92518-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92518-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92518-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92518-114">**.NET Framework Versions:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92518-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92518-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="92518-115">See also</span></span>

- [<span data-ttu-id="92518-116">Interface ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="92518-116">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="92518-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="92518-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
