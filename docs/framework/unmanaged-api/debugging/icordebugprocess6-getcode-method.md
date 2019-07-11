---
title: Método ICorDebugProcess6::GetCode
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 810590f0d1f7f74b778d73d98a9f7f9b1988b75f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736446"
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="d7cde-102">Método ICorDebugProcess6::GetCode</span><span class="sxs-lookup"><span data-stu-id="d7cde-102">ICorDebugProcess6::GetCode Method</span></span>
<span data-ttu-id="d7cde-103">Obtém informações sobre o código gerenciado em um endereço de código em particular.</span><span class="sxs-lookup"><span data-stu-id="d7cde-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7cde-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d7cde-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,   
    [out] ICorDebugCode **ppCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7cde-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d7cde-105">Parameters</span></span>  
 `codeAddress`  
 <span data-ttu-id="d7cde-106">[in] Um [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) valor que especifica o endereço inicial do segmento de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d7cde-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="d7cde-107">[out] Um ponteiro para o endereço de um objeto de "ICorDebugCode" que representa um segmento de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d7cde-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7cde-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="d7cde-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7cde-109">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d7cde-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7cde-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d7cde-110">Requirements</span></span>  
 <span data-ttu-id="d7cde-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7cde-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7cde-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7cde-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7cde-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7cde-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7cde-114">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7cde-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7cde-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7cde-115">See also</span></span>

- [<span data-ttu-id="d7cde-116">Interface ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="d7cde-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="d7cde-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="d7cde-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
