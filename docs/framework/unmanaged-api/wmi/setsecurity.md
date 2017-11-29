---
title: "Função SetSecurity (referência de API não gerenciada)"
description: "A função SetSecurity recupera o token de representação do thread atual."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: SetSecurity
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: SetSecurity
helpviewer_keywords: SetSecurity function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4fd7ccb0cfb25773da7e489f9ce4d6332b80a616
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="setsecurity-function"></a><span data-ttu-id="cbb9c-103">Função SetSecurity</span><span class="sxs-lookup"><span data-stu-id="cbb9c-103">SetSecurity function</span></span>
<span data-ttu-id="cbb9c-104">Recupera o token de representação associado ao segmento atual.</span><span class="sxs-lookup"><span data-stu-id="cbb9c-104">Retrieves the impersonation token associated with the current thread.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="cbb9c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cbb9c-105">Syntax</span></span>  
  
```  
HRESULT SetSecurity (
   [out] boolean* pNeedToReset, 
   [out] HANDLE* pCurrentThreadToken
); 
```  

## <a name="parameters"></a><span data-ttu-id="cbb9c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cbb9c-106">Parameters</span></span>

<span data-ttu-id="cbb9c-107">`pNeedToReset`[out] Quando a função retornar, contém um ponteiro para um `boolean` que indica se o token deve ser redefinido chamando o [ResetSecurity](resetsecurity.md) função.</span><span class="sxs-lookup"><span data-stu-id="cbb9c-107">`pNeedToReset` [out] When the function returns, contains a pointer to a `boolean` that indicates whether the token should be reset by calling the [ResetSecurity](resetsecurity.md) function.</span></span>  

`token`  
<span data-ttu-id="cbb9c-108">[out] Quando a função retornar, contém um ponteiro para o identificador de token de representação associado ao segmento atual.</span><span class="sxs-lookup"><span data-stu-id="cbb9c-108">[out] When the function returns, contains a pointer to the handle of the impersonation token associated with the current thread.</span></span> <span data-ttu-id="cbb9c-109">Seu valor pode ser `null` se não houver nenhum token associado ao segmento atual.</span><span class="sxs-lookup"><span data-stu-id="cbb9c-109">Its value can be `null` if there is no token associated with the current thread.</span></span> 

## <a name="return-value"></a><span data-ttu-id="cbb9c-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="cbb9c-110">Return value</span></span>

<span data-ttu-id="cbb9c-111">Se a função tiver êxito, o valor de retorno é `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="cbb9c-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="cbb9c-112">Se a função falhar, o valor de retorno é um código de erro diferente de zero.</span><span class="sxs-lookup"><span data-stu-id="cbb9c-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="cbb9c-113">Para obter mais informações sobre o erro, chame o [GetErrorInfo](geterrorinfo.md) função.</span><span class="sxs-lookup"><span data-stu-id="cbb9c-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="cbb9c-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cbb9c-114">Requirements</span></span>  
 <span data-ttu-id="cbb9c-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbb9c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbb9c-116">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="cbb9c-116">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="cbb9c-117">**Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="cbb9c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbb9c-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cbb9c-118">See also</span></span>  
[<span data-ttu-id="cbb9c-119">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="cbb9c-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
