---
title: "Método ICorDebugProcess6::GetCode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c69ce290a486960978ddaf87203328df4f392b48
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="db28e-102">Método ICorDebugProcess6::GetCode</span><span class="sxs-lookup"><span data-stu-id="db28e-102">ICorDebugProcess6::GetCode Method</span></span>
<span data-ttu-id="db28e-103">Obtém informações sobre o código gerenciado em um endereço de código em particular.</span><span class="sxs-lookup"><span data-stu-id="db28e-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db28e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="db28e-104">Syntax</span></span>  
  
```  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,   
    [out] ICorDebugCode **ppCode);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db28e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="db28e-105">Parameters</span></span>  
 `codeAddress`  
 <span data-ttu-id="db28e-106">[in] Um [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) valor que especifica o endereço inicial do segmento de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="db28e-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="db28e-107">[out] Um ponteiro para o endereço de um objeto de "ICorDebugCode" que representa um segmento de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="db28e-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db28e-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="db28e-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="db28e-109">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="db28e-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db28e-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="db28e-110">Requirements</span></span>  
 <span data-ttu-id="db28e-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db28e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db28e-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="db28e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="db28e-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="db28e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db28e-114">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db28e-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db28e-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db28e-115">See Also</span></span>  
 [<span data-ttu-id="db28e-116">Interface ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="db28e-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [<span data-ttu-id="db28e-117">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="db28e-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
