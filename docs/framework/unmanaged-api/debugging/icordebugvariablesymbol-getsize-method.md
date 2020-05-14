---
title: 'Método ICorDebugVariableSymbol:: GetSize'
ms.date: 03/30/2017
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
ms.openlocfilehash: d924de33c8ec49501be0ee7700b2eee8c79bb950
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397118"
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="8eb8a-102">Método ICorDebugVariableSymbol:: GetSize</span><span class="sxs-lookup"><span data-stu-id="8eb8a-102">ICorDebugVariableSymbol::GetSize Method</span></span>
<span data-ttu-id="8eb8a-103">Obtém o tamanho de uma variável em bytes.</span><span class="sxs-lookup"><span data-stu-id="8eb8a-103">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8eb8a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8eb8a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8eb8a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8eb8a-105">Parameters</span></span>  
 `pcbValue`  
 <span data-ttu-id="8eb8a-106">Um ponteiro para um inteiro sem sinal de 32 bits contendo o tamanho da variável.</span><span class="sxs-lookup"><span data-stu-id="8eb8a-106">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8eb8a-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="8eb8a-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8eb8a-108">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8eb8a-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8eb8a-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8eb8a-109">Requirements</span></span>  
 <span data-ttu-id="8eb8a-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8eb8a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8eb8a-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8eb8a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8eb8a-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8eb8a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8eb8a-113">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8eb8a-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eb8a-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="8eb8a-114">See also</span></span>

- [<span data-ttu-id="8eb8a-115">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="8eb8a-115">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="8eb8a-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="8eb8a-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
