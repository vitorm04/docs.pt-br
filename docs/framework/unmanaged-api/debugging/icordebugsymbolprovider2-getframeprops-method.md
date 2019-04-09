---
title: Método ICorDebugSymbolProvider2::GetFrameProps
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b20d78abbfa1db43047872a596289028833de37d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098982"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="c15d9-102">Método ICorDebugSymbolProvider2::GetFrameProps</span><span class="sxs-lookup"><span data-stu-id="c15d9-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>
<span data-ttu-id="c15d9-103">Retorna o método Iniciando endereço virtual relativo de um método e o quadro pai recebe um endereço virtual relativo de código.</span><span class="sxs-lookup"><span data-stu-id="c15d9-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c15d9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c15d9-104">Syntax</span></span>  
  
```  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c15d9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c15d9-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="c15d9-106">[in] Um endereço virtual relativo de código.</span><span class="sxs-lookup"><span data-stu-id="c15d9-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="c15d9-107">[out] Um ponteiro para o método Iniciando endereço virtual relativo.</span><span class="sxs-lookup"><span data-stu-id="c15d9-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="c15d9-108">[out] Um ponteiro para o quadro Iniciando endereço virtual relativo.</span><span class="sxs-lookup"><span data-stu-id="c15d9-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c15d9-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="c15d9-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c15d9-110">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c15d9-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c15d9-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c15d9-111">Requirements</span></span>  
 <span data-ttu-id="c15d9-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c15d9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c15d9-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c15d9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c15d9-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c15d9-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="c15d9-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="c15d9-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c15d9-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c15d9-116">See also</span></span>

- [<span data-ttu-id="c15d9-117">Interface ICorDebugSymbolProvider2</span><span class="sxs-lookup"><span data-stu-id="c15d9-117">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="c15d9-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="c15d9-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
