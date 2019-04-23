---
title: Método ICorDebugProcess6::MarkDebuggerAttached
ms.date: 03/30/2017
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 15e2e94ac4e30fbdb375175148a5b448c51821f0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59128018"
---
# <a name="icordebugprocess6markdebuggerattached-method"></a><span data-ttu-id="ba244-102">Método ICorDebugProcess6::MarkDebuggerAttached</span><span class="sxs-lookup"><span data-stu-id="ba244-102">ICorDebugProcess6::MarkDebuggerAttached Method</span></span>
<span data-ttu-id="ba244-103">Altera o estado interno do depurado para que o método <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> na biblioteca de classes .NET Framework retorne `true`.</span><span class="sxs-lookup"><span data-stu-id="ba244-103">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba244-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ba244-104">Syntax</span></span>  
  
```  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba244-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ba244-105">Parameters</span></span>  
 `fIsAttached`  
 <span data-ttu-id="ba244-106">`true` se o método <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> deve indicar que um depurador é anexado; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="ba244-106">`true` if the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method should indicate that a debugger is attached; `false` otherwise.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ba244-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ba244-107">Return Value</span></span>  
 <span data-ttu-id="ba244-108">O método pode retornar os valores listados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="ba244-108">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="ba244-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="ba244-109">Return value</span></span>|<span data-ttu-id="ba244-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="ba244-110">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="ba244-111">A depuração foi atualizada com êxito.</span><span class="sxs-lookup"><span data-stu-id="ba244-111">The debuggee was successfully updated.</span></span>|  
|`CORDBG_E_MODULE_NOT_LOADED`|<span data-ttu-id="ba244-112">O assembly que contém o método <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> não é carregado, ou outros erros como metadados ausentes estão impedindo que ele seja reconhecido.</span><span class="sxs-lookup"><span data-stu-id="ba244-112">The assembly that contains the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method is not loaded, or some other error, such as missing metadata, is preventing it from being recognized.</span></span><br /><br /> <span data-ttu-id="ba244-113">Esse erro é comum e benigno.</span><span class="sxs-lookup"><span data-stu-id="ba244-113">This error is common and benign.</span></span> <span data-ttu-id="ba244-114">Você deve chamar o método novamente ao carregar assemblies adicionais.</span><span class="sxs-lookup"><span data-stu-id="ba244-114">You should call the method again when additional assemblies load.</span></span>|  
|<span data-ttu-id="ba244-115">Outros valores `HRESULT` com falha.</span><span class="sxs-lookup"><span data-stu-id="ba244-115">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="ba244-116">Outros valores provavelmente indicam depurador ou componentes do compilador com comportamento inadequado.</span><span class="sxs-lookup"><span data-stu-id="ba244-116">Other values likely indicate misbehaving debugger or compiler components.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba244-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="ba244-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ba244-118">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ba244-118">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba244-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ba244-119">Requirements</span></span>  
 <span data-ttu-id="ba244-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba244-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba244-121">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba244-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba244-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba244-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba244-123">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba244-123">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba244-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba244-124">See also</span></span>

- [<span data-ttu-id="ba244-125">Interface ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="ba244-125">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="ba244-126">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="ba244-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
