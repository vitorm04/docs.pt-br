---
title: "Método ICorDebugSymbolProvider2::GetFrameProps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3892b8da3286132709792513f055d6ce75bd3fce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="b94db-102">Método ICorDebugSymbolProvider2::GetFrameProps</span><span class="sxs-lookup"><span data-stu-id="b94db-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>
<span data-ttu-id="b94db-103">Retorna o método Iniciando endereço virtual relativo de um método e o quadro pai recebe um endereço virtual relativo de código.</span><span class="sxs-lookup"><span data-stu-id="b94db-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b94db-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b94db-104">Syntax</span></span>  
  
```  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b94db-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b94db-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="b94db-106">[in] Um endereço virtual relativo de código.</span><span class="sxs-lookup"><span data-stu-id="b94db-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="b94db-107">[out] Um ponteiro para o método Iniciando endereço virtual relativo.</span><span class="sxs-lookup"><span data-stu-id="b94db-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="b94db-108">[out] Um ponteiro para o quadro Iniciando endereço virtual relativo.</span><span class="sxs-lookup"><span data-stu-id="b94db-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b94db-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="b94db-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b94db-110">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b94db-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b94db-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b94db-111">Requirements</span></span>  
 <span data-ttu-id="b94db-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b94db-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b94db-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b94db-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b94db-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b94db-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b94db-115">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b94db-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b94db-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b94db-116">See Also</span></span>  
 [<span data-ttu-id="b94db-117">Interface ICorDebugSymbolProvider2</span><span class="sxs-lookup"><span data-stu-id="b94db-117">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 [<span data-ttu-id="b94db-118">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="b94db-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
