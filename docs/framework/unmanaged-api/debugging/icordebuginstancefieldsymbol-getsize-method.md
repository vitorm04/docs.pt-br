---
title: 'Método ICorDebugInstanceFieldSymbol:: GetSize'
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
ms.openlocfilehash: eb70c441441954e2ffce6ca832c58369c606b128
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782275"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="4986a-102">Método ICorDebugInstanceFieldSymbol:: GetSize</span><span class="sxs-lookup"><span data-stu-id="4986a-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="4986a-103">Obtém o tamanho em bytes do campo de instância.</span><span class="sxs-lookup"><span data-stu-id="4986a-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4986a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4986a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4986a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4986a-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="4986a-106">fora Um ponteiro para o comprimento do campo.</span><span class="sxs-lookup"><span data-stu-id="4986a-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4986a-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="4986a-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4986a-108">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4986a-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4986a-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="4986a-109">Requirements</span></span>  
 <span data-ttu-id="4986a-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4986a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4986a-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4986a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4986a-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4986a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4986a-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4986a-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4986a-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="4986a-114">See also</span></span>

- [<span data-ttu-id="4986a-115">Interface ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="4986a-115">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="4986a-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="4986a-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
