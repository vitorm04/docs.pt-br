---
title: "Método ICorDebugILFrame::CanSetIP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.CanSetIP
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::CanSetIP
helpviewer_keywords:
- CanSetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::CanSetIP method [.NET Framework debugging]
ms.assetid: 16caf02f-c71e-486c-90b0-f0e54357d8f0
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bbb5b0a8038445372b5e404fac554c0726353bf6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugilframecansetip-method"></a><span data-ttu-id="82aaa-102">Método ICorDebugILFrame::CanSetIP</span><span class="sxs-lookup"><span data-stu-id="82aaa-102">ICorDebugILFrame::CanSetIP Method</span></span>
<span data-ttu-id="82aaa-103">Obtém o HRESULT que indica se é seguro definir o ponteiro de instrução para o local de deslocamento especificado no código do Microsoft Intermediate Language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="82aaa-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer to the specified offset location in Microsoft Intermediate Language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82aaa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="82aaa-104">Syntax</span></span>  
  
```  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="82aaa-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="82aaa-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="82aaa-106">[in] A configuração desejada para o ponteiro de instrução.</span><span class="sxs-lookup"><span data-stu-id="82aaa-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82aaa-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="82aaa-107">Remarks</span></span>  
 <span data-ttu-id="82aaa-108">Use o `CanSetIP` método antes de chamar o [Icordebugilframe](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="82aaa-108">Use the `CanSetIP` method before calling the [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) method.</span></span> <span data-ttu-id="82aaa-109">Se `CanSetIP` retorna qualquer HRESULT que não sejam S_OK, você ainda pode invocar `ICorDebugILFrame::SetIP`, mas não há nenhuma garantia de que o depurador continuará a execução correta e segura do código que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="82aaa-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugILFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82aaa-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="82aaa-110">Requirements</span></span>  
 <span data-ttu-id="82aaa-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82aaa-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82aaa-112">**Cabeçalho:** CorDebug.idl, CorDebug, h</span><span class="sxs-lookup"><span data-stu-id="82aaa-112">**Header:** CorDebug.idl, CorDebug,h</span></span>  
  
 <span data-ttu-id="82aaa-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82aaa-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82aaa-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82aaa-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
