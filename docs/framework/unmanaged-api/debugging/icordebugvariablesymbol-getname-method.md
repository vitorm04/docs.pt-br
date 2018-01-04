---
title: "Método ICorDebugVariableSymbol::GetName"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 747249c23089cbeba04c3a872823f01f2b334203
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="cc167-102">Método ICorDebugVariableSymbol::GetName</span><span class="sxs-lookup"><span data-stu-id="cc167-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="cc167-103">Obtém o nome de uma variável.</span><span class="sxs-lookup"><span data-stu-id="cc167-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc167-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cc167-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cc167-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cc167-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="cc167-106">[in] O número de caracteres a `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="cc167-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="cc167-107">[out] Um ponteiro para o número de caracteres gravados o `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="cc167-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="cc167-108">Um ponteiro para uma matriz de caracteres que contém o nome da variável.</span><span class="sxs-lookup"><span data-stu-id="cc167-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc167-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="cc167-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc167-110">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="cc167-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc167-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cc167-111">Requirements</span></span>  
 <span data-ttu-id="cc167-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc167-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc167-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc167-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc167-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc167-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc167-115">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc167-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc167-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc167-116">See Also</span></span>  
 [<span data-ttu-id="cc167-117">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="cc167-117">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="cc167-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="cc167-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
