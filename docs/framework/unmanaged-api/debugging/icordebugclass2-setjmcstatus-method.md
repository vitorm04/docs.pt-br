---
title: "Método ICorDebugClass2::SetJMCStatus"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugClass2.SetJMCStatus
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugClass2::SetJMCStatus
helpviewer_keywords:
- ICorDebugClass2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 077e6c7f-f857-480c-bebb-76ee1de4e8fc
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: da9f61bd9a652b4c8e340ddecdee4b48bbdb086e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugclass2setjmcstatus-method"></a><span data-ttu-id="04a96-102">Método ICorDebugClass2::SetJMCStatus</span><span class="sxs-lookup"><span data-stu-id="04a96-102">ICorDebugClass2::SetJMCStatus Method</span></span>
<span data-ttu-id="04a96-103">Para cada método da classe, define um valor que indica se o método é código definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="04a96-103">For each method of the class, sets a value that indicates whether the method is user-defined code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04a96-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="04a96-104">Syntax</span></span>  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="04a96-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="04a96-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="04a96-106">[in] Definido como `true` para indicar que o método é definido pelo usuário código; caso contrário, é definido como `false`.</span><span class="sxs-lookup"><span data-stu-id="04a96-106">[in] Set to `true` to indicate that the method is user-defined code; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04a96-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="04a96-107">Remarks</span></span>  
 <span data-ttu-id="04a96-108">Um seletor de (JMC) apenas meu código vai ignorar código definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="04a96-108">A just-my-code (JMC) stepper will skip non-user-defined code.</span></span> <span data-ttu-id="04a96-109">Código definido pelo usuário deve ser um subconjunto de código depurável.</span><span class="sxs-lookup"><span data-stu-id="04a96-109">User-defined code must be a subset of debuggable code.</span></span>  
  
 <span data-ttu-id="04a96-110">`SetJMCStatus`Retorna um valor HRESULT S_FALSE se ele falhar ao definir o valor de qualquer método, mesmo que ele define o valor para todos os outros métodos com êxito.</span><span class="sxs-lookup"><span data-stu-id="04a96-110">`SetJMCStatus` returns an HRESULT value of S_FALSE if it fails to set the value for any method, even if it successfully sets the value for all other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04a96-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="04a96-111">Requirements</span></span>  
 <span data-ttu-id="04a96-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04a96-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04a96-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="04a96-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04a96-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04a96-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04a96-115">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04a96-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
