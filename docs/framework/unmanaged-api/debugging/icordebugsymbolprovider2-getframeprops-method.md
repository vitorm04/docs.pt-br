---
title: Método ICorDebugSymbolProvider2::GetFrameProps
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 274da030bbbb7c614709b5150f08f37ddf5aaf5a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771169"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="05abd-102">Método ICorDebugSymbolProvider2::GetFrameProps</span><span class="sxs-lookup"><span data-stu-id="05abd-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>
<span data-ttu-id="05abd-103">Retorna o método Iniciando endereço virtual relativo de um método e o quadro pai recebe um endereço virtual relativo de código.</span><span class="sxs-lookup"><span data-stu-id="05abd-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05abd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="05abd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05abd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="05abd-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="05abd-106">[in] Um endereço virtual relativo de código.</span><span class="sxs-lookup"><span data-stu-id="05abd-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="05abd-107">[out] Um ponteiro para o método Iniciando endereço virtual relativo.</span><span class="sxs-lookup"><span data-stu-id="05abd-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="05abd-108">[out] Um ponteiro para o quadro Iniciando endereço virtual relativo.</span><span class="sxs-lookup"><span data-stu-id="05abd-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05abd-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="05abd-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05abd-110">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="05abd-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05abd-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="05abd-111">Requirements</span></span>  
 <span data-ttu-id="05abd-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05abd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05abd-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="05abd-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="05abd-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05abd-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05abd-115">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05abd-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05abd-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="05abd-116">See also</span></span>

- [<span data-ttu-id="05abd-117">Interface ICorDebugSymbolProvider2</span><span class="sxs-lookup"><span data-stu-id="05abd-117">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="05abd-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="05abd-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
