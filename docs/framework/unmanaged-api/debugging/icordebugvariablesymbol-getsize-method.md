---
title: "Método ICorDebugVariableSymbol::GetSize"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0ea4a77b08b12c3f067d51f9dfe2c961192c3354
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="9aaa7-102">Método ICorDebugVariableSymbol::GetSize</span><span class="sxs-lookup"><span data-stu-id="9aaa7-102">ICorDebugVariableSymbol::GetSize Method</span></span>
<span data-ttu-id="9aaa7-103">Obtém o tamanho de uma variável em bytes.</span><span class="sxs-lookup"><span data-stu-id="9aaa7-103">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9aaa7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9aaa7-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9aaa7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9aaa7-105">Parameters</span></span>  
 `pcbValue`  
 <span data-ttu-id="9aaa7-106">Um ponteiro para um inteiro não assinado de 32 bits que contém o tamanho da variável.</span><span class="sxs-lookup"><span data-stu-id="9aaa7-106">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9aaa7-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="9aaa7-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9aaa7-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9aaa7-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9aaa7-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9aaa7-109">Requirements</span></span>  
 <span data-ttu-id="9aaa7-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9aaa7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9aaa7-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9aaa7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9aaa7-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9aaa7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9aaa7-113">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9aaa7-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9aaa7-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9aaa7-114">See Also</span></span>  
 [<span data-ttu-id="9aaa7-115">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="9aaa7-115">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="9aaa7-116">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="9aaa7-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
