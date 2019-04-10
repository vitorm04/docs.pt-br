---
title: Método ICorDebugVariableSymbol::GetSize
ms.date: 03/30/2017
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 027b3f773ff0ed0ca7bf9d193f97a3b060ea8494
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211836"
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="908ad-102">Método ICorDebugVariableSymbol::GetSize</span><span class="sxs-lookup"><span data-stu-id="908ad-102">ICorDebugVariableSymbol::GetSize Method</span></span>
<span data-ttu-id="908ad-103">Obtém o tamanho de uma variável em bytes.</span><span class="sxs-lookup"><span data-stu-id="908ad-103">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="908ad-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="908ad-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="908ad-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="908ad-105">Parameters</span></span>  
 `pcbValue`  
 <span data-ttu-id="908ad-106">Um ponteiro para um inteiro sem sinal de 32 bits que contém o tamanho da variável.</span><span class="sxs-lookup"><span data-stu-id="908ad-106">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="908ad-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="908ad-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="908ad-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="908ad-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="908ad-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="908ad-109">Requirements</span></span>  
 <span data-ttu-id="908ad-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="908ad-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="908ad-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="908ad-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="908ad-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="908ad-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="908ad-113">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="908ad-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="908ad-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="908ad-114">See also</span></span>

- [<span data-ttu-id="908ad-115">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="908ad-115">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="908ad-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="908ad-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
