---
title: Método ICorDebugAppDomain::GetObject
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetObject
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetObject
helpviewer_keywords:
- ICorDebugAppDomain::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 78232e6f-ae18-4cfa-a6cd-e79471cf9d76
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0ca9792df69f859e20f1d9e40754d1cec138945d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480020"
---
# <a name="icordebugappdomaingetobject-method"></a><span data-ttu-id="d8bf2-102">Método ICorDebugAppDomain::GetObject</span><span class="sxs-lookup"><span data-stu-id="d8bf2-102">ICorDebugAppDomain::GetObject Method</span></span>
<span data-ttu-id="d8bf2-103">Obtém um ponteiro de interface para o domínio de aplicativo do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="d8bf2-103">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8bf2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d8bf2-104">Syntax</span></span>  
  
```  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8bf2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d8bf2-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="d8bf2-106">[out] Um ponteiro para o endereço de um objeto de interface ICorDebugValue que representa o domínio do aplicativo CLR.</span><span class="sxs-lookup"><span data-stu-id="d8bf2-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d8bf2-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d8bf2-107">Return Value</span></span>  
 <span data-ttu-id="d8bf2-108">Se um gerenciado <xref:System.AppDomain?displayProperty=nameWithType> objeto ainda não foi construído para esse domínio de aplicativo, o método retornará `S_FALSE` e coloca `NULL` em `*ppObject`.</span><span class="sxs-lookup"><span data-stu-id="d8bf2-108">If a managed <xref:System.AppDomain?displayProperty=nameWithType> object hasn't been constructed for this application domain, the method returns `S_FALSE` and places `NULL` in `*ppObject`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8bf2-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="d8bf2-109">Remarks</span></span>  
 <span data-ttu-id="d8bf2-110">Cada domínio de aplicativo em um processo pode ter um gerenciado <xref:System.AppDomain?displayProperty=nameWithType> objeto no tempo de execução que o representa.</span><span class="sxs-lookup"><span data-stu-id="d8bf2-110">Each application domain in a process may have a managed <xref:System.AppDomain?displayProperty=nameWithType> object in the runtime that represents it.</span></span> <span data-ttu-id="d8bf2-111">Essa função obtém um objeto de interface ICorDebugValue que corresponde a este gerenciado <xref:System.AppDomain?displayProperty=nameWithType> objeto.</span><span class="sxs-lookup"><span data-stu-id="d8bf2-111">This function gets an ICorDebugValue interface object that corresponds to this managed <xref:System.AppDomain?displayProperty=nameWithType> object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8bf2-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d8bf2-112">Requirements</span></span>  
 <span data-ttu-id="d8bf2-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8bf2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8bf2-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8bf2-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8bf2-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8bf2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8bf2-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8bf2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
