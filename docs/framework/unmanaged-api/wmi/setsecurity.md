---
title: Função SetSecurity (referência de API não gerenciada)
description: A função SetSecurity recupera o token de representação do thread atual.
ms.date: 11/06/2017
api_name:
- SetSecurity
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SetSecurity
helpviewer_keywords:
- SetSecurity function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b3e8ddb34849611daae4dfa1d2762a25ac5cf82
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54721130"
---
# <a name="setsecurity-function"></a><span data-ttu-id="958d4-103">Função SetSecurity</span><span class="sxs-lookup"><span data-stu-id="958d4-103">SetSecurity function</span></span>
<span data-ttu-id="958d4-104">Recupera o token de representação associado ao thread atual.</span><span class="sxs-lookup"><span data-stu-id="958d4-104">Retrieves the impersonation token associated with the current thread.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="958d4-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="958d4-105">Syntax</span></span>  
  
```  
HRESULT SetSecurity (
   [out] boolean* pNeedToReset, 
   [out] HANDLE* pCurrentThreadToken
); 
```  

## <a name="parameters"></a><span data-ttu-id="958d4-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="958d4-106">Parameters</span></span>

<span data-ttu-id="958d4-107">`pNeedToReset` [out] Quando a função retorna, contém um ponteiro para um `boolean` que indica se o token deve ser redefinido por meio da chamada a [ResetSecurity](resetsecurity.md) função.</span><span class="sxs-lookup"><span data-stu-id="958d4-107">`pNeedToReset` [out] When the function returns, contains a pointer to a `boolean` that indicates whether the token should be reset by calling the [ResetSecurity](resetsecurity.md) function.</span></span>  

`token`  
<span data-ttu-id="958d4-108">[out] Quando a função retornar, contém um ponteiro para o identificador do token de representação associado ao thread atual.</span><span class="sxs-lookup"><span data-stu-id="958d4-108">[out] When the function returns, contains a pointer to the handle of the impersonation token associated with the current thread.</span></span> <span data-ttu-id="958d4-109">Seu valor pode ser `null` se não houver nenhum token associado ao thread atual.</span><span class="sxs-lookup"><span data-stu-id="958d4-109">Its value can be `null` if there is no token associated with the current thread.</span></span> 

## <a name="return-value"></a><span data-ttu-id="958d4-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="958d4-110">Return value</span></span>

<span data-ttu-id="958d4-111">Se a função for bem-sucedida, o valor retornado é `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="958d4-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="958d4-112">Se a função falhar, o valor de retorno é um código de erro diferente de zero.</span><span class="sxs-lookup"><span data-stu-id="958d4-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="958d4-113">Para obter outras informações de erro, chame o [GetErrorInfo](geterrorinfo.md) função.</span><span class="sxs-lookup"><span data-stu-id="958d4-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="958d4-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="958d4-114">Requirements</span></span>  
 <span data-ttu-id="958d4-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="958d4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="958d4-116">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="958d4-116">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="958d4-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="958d4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="958d4-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="958d4-118">See also</span></span>
- [<span data-ttu-id="958d4-119">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="958d4-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
