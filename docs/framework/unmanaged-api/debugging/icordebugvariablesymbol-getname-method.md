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
ms.openlocfilehash: aff18efb6781aee5b6a148fcd59863a2ce657023
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="a1357-102">Método ICorDebugVariableSymbol::GetName</span><span class="sxs-lookup"><span data-stu-id="a1357-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="a1357-103">Obtém o nome de uma variável.</span><span class="sxs-lookup"><span data-stu-id="a1357-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1357-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a1357-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a1357-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a1357-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="a1357-106">[in] O número de caracteres a `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="a1357-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="a1357-107">[out] Um ponteiro para o número de caracteres gravados o `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="a1357-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="a1357-108">Um ponteiro para uma matriz de caracteres que contém o nome da variável.</span><span class="sxs-lookup"><span data-stu-id="a1357-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1357-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="a1357-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a1357-110">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a1357-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1357-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a1357-111">Requirements</span></span>  
 <span data-ttu-id="a1357-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1357-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1357-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a1357-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a1357-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1357-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1357-115">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1357-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1357-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1357-116">See Also</span></span>  
 [<span data-ttu-id="a1357-117">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="a1357-117">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="a1357-118">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="a1357-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
