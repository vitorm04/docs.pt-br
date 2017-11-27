---
title: "Método ICorDebugAppDomain::GetObject"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.GetObject
api_location: corguids.lib
api_type: COM
f1_keywords: ICorDebugAppDomain::GetObject
helpviewer_keywords:
- ICorDebugAppDomain::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 78232e6f-ae18-4cfa-a6cd-e79471cf9d76
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c4f923d8e9bf9762d5208dd6e9be527a50a688b1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomaingetobject-method"></a><span data-ttu-id="0719d-102">Método ICorDebugAppDomain::GetObject</span><span class="sxs-lookup"><span data-stu-id="0719d-102">ICorDebugAppDomain::GetObject Method</span></span>
<span data-ttu-id="0719d-103">Obtém um ponteiro de interface para o domínio de aplicativo do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="0719d-103">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0719d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0719d-104">Syntax</span></span>  
  
```  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0719d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0719d-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="0719d-106">[out] Um ponteiro para o endereço de um objeto de interface ICorDebugValue que representa o domínio do aplicativo CLR.</span><span class="sxs-lookup"><span data-stu-id="0719d-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0719d-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0719d-107">Return Value</span></span>  
 <span data-ttu-id="0719d-108">Se um gerenciado <xref:System.AppDomain?displayProperty=nameWithType> objeto ainda não foi construído para esse domínio de aplicativo, o método retorna `S_FALSE` e coloca `NULL` em `*ppObject`.</span><span class="sxs-lookup"><span data-stu-id="0719d-108">If a managed <xref:System.AppDomain?displayProperty=nameWithType> object hasn't been constructed for this application domain, the method returns `S_FALSE` and places `NULL` in `*ppObject`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0719d-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="0719d-109">Remarks</span></span>  
 <span data-ttu-id="0719d-110">Cada domínio de aplicativo em um processo pode ter um gerenciado <xref:System.AppDomain?displayProperty=nameWithType> objeto em tempo de execução que o representa.</span><span class="sxs-lookup"><span data-stu-id="0719d-110">Each application domain in a process may have a managed <xref:System.AppDomain?displayProperty=nameWithType> object in the runtime that represents it.</span></span> <span data-ttu-id="0719d-111">Esta função obtém um objeto de interface ICorDebugValue que corresponde a este gerenciado <xref:System.AppDomain?displayProperty=nameWithType> objeto.</span><span class="sxs-lookup"><span data-stu-id="0719d-111">This function gets an ICorDebugValue interface object that corresponds to this managed <xref:System.AppDomain?displayProperty=nameWithType> object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0719d-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0719d-112">Requirements</span></span>  
 <span data-ttu-id="0719d-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0719d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0719d-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0719d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0719d-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0719d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0719d-116">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0719d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
