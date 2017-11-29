---
title: "Método ICorDebugEval::NewString"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.NewString
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::NewString
helpviewer_keywords:
- NewString method [.NET Framework debugging]
- ICorDebugEval::NewString method [.NET Framework debugging]
ms.assetid: 29e7a14b-d50e-4852-bfda-011b76c0c9ee
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 48c1a36e32feb94e8399c46f88a98f75c81fdb6a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugevalnewstring-method"></a><span data-ttu-id="34317-102">Método ICorDebugEval::NewString</span><span class="sxs-lookup"><span data-stu-id="34317-102">ICorDebugEval::NewString Method</span></span>
<span data-ttu-id="34317-103">Aloca uma nova instância da cadeia de caracteres com o conteúdo especificado.</span><span class="sxs-lookup"><span data-stu-id="34317-103">Allocates a new string instance with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34317-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="34317-104">Syntax</span></span>  
  
```  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="34317-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34317-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="34317-106">[in] Ponteiro para o conteúdo para a cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="34317-106">[in] Pointer to the contents for the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34317-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="34317-107">Remarks</span></span>  
 <span data-ttu-id="34317-108">A cadeia de caracteres sempre é criada no domínio do aplicativo no qual o thread está em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="34317-108">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34317-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="34317-109">Requirements</span></span>  
 <span data-ttu-id="34317-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34317-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34317-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="34317-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="34317-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34317-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34317-113">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34317-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
