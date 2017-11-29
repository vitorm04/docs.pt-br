---
title: "Método ICorDebugDataTarget2::GetSymbolProviderForImage"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b7c0a2f0-e904-43b3-98e1-d669e8a589e8
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 868e1e8d670a438d7a93bfac27f213c9c35ea58c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget2getsymbolproviderforimage-method"></a><span data-ttu-id="a7e36-102">Método ICorDebugDataTarget2::GetSymbolProviderForImage</span><span class="sxs-lookup"><span data-stu-id="a7e36-102">ICorDebugDataTarget2::GetSymbolProviderForImage Method</span></span>
<span data-ttu-id="a7e36-103">Retorna o provedor de símbolo para um módulo do endereço base do módulo.</span><span class="sxs-lookup"><span data-stu-id="a7e36-103">Returns the symbol-provider for a module from the base address of that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7e36-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a7e36-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolProviderForImage(  
    [in] CORDB_ADDRESS imageBaseAddress,   
    [out] ICorDebugSymbolProvider **ppSymProvider  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a7e36-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a7e36-105">Parameters</span></span>  
 `imageBaseAddress`  
 <span data-ttu-id="a7e36-106">[in] Um [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) valor que representa o endereço base de um módulo.</span><span class="sxs-lookup"><span data-stu-id="a7e36-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the base address of a module.</span></span>  
  
 `ppSymProvider`  
 <span data-ttu-id="a7e36-107">[out] Um ponteiro para o endereço de um [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="a7e36-107">[out] A pointer to the address of an [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7e36-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="a7e36-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7e36-109">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a7e36-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7e36-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a7e36-110">Requirements</span></span>  
 <span data-ttu-id="a7e36-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7e36-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7e36-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a7e36-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7e36-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7e36-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7e36-114">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7e36-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7e36-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7e36-115">See Also</span></span>  
 [<span data-ttu-id="a7e36-116">Interface ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="a7e36-116">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="a7e36-117">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="a7e36-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
