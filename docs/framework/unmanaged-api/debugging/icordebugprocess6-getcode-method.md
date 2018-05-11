---
title: Método ICorDebugProcess6::GetCode
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 572b279ddfdb1fb0eb9da4b0d1f8c2cb12c8a46b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="26700-102">Método ICorDebugProcess6::GetCode</span><span class="sxs-lookup"><span data-stu-id="26700-102">ICorDebugProcess6::GetCode Method</span></span>
<span data-ttu-id="26700-103">Obtém informações sobre o código gerenciado em um endereço de código em particular.</span><span class="sxs-lookup"><span data-stu-id="26700-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26700-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="26700-104">Syntax</span></span>  
  
```  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,   
    [out] ICorDebugCode **ppCode);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="26700-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="26700-105">Parameters</span></span>  
 `codeAddress`  
 <span data-ttu-id="26700-106">[in] Um [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) valor que especifica o endereço inicial do segmento de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="26700-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="26700-107">[out] Um ponteiro para o endereço de um objeto de "ICorDebugCode" que representa um segmento de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="26700-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26700-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="26700-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="26700-109">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="26700-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26700-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="26700-110">Requirements</span></span>  
 <span data-ttu-id="26700-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26700-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26700-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="26700-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="26700-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26700-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26700-114">**Versões do .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26700-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26700-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26700-115">See Also</span></span>  
 [<span data-ttu-id="26700-116">Interface ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="26700-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [<span data-ttu-id="26700-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="26700-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
