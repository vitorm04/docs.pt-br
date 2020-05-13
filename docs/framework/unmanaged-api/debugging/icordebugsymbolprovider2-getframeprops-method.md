---
title: 'Método ICorDebugSymbolProvider2:: GetFrameProps'
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
ms.openlocfilehash: ad44c5a7b2d901967ae354f3c30218a8c7f2c2de
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379332"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="6db5c-102">Método ICorDebugSymbolProvider2:: GetFrameProps</span><span class="sxs-lookup"><span data-stu-id="6db5c-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>
<span data-ttu-id="6db5c-103">Retorna o método iniciando o endereço virtual relativo de um método e o quadro pai, dado um endereço virtual relativo de código.</span><span class="sxs-lookup"><span data-stu-id="6db5c-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6db5c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6db5c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6db5c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6db5c-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="6db5c-106">no Um endereço virtual relativo ao código.</span><span class="sxs-lookup"><span data-stu-id="6db5c-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="6db5c-107">fora Um ponteiro para o endereço virtual relativo inicial do método.</span><span class="sxs-lookup"><span data-stu-id="6db5c-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="6db5c-108">fora Um ponteiro para o endereço virtual relativo inicial do quadro.</span><span class="sxs-lookup"><span data-stu-id="6db5c-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6db5c-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="6db5c-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6db5c-110">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6db5c-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6db5c-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6db5c-111">Requirements</span></span>  
 <span data-ttu-id="6db5c-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6db5c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6db5c-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6db5c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6db5c-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6db5c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6db5c-115">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6db5c-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6db5c-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="6db5c-116">See also</span></span>

- [<span data-ttu-id="6db5c-117">Interface ICorDebugSymbolProvider2</span><span class="sxs-lookup"><span data-stu-id="6db5c-117">ICorDebugSymbolProvider2 Interface</span></span>](icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="6db5c-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="6db5c-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
