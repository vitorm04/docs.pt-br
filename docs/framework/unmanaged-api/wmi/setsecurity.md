---
title: Função setsecurity (referência de API não gerenciada)
description: A função setsecurity recupera o token de representação do thread atual.
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
ms.openlocfilehash: 94c76213acb66116105d181e9961a33976047ee7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798244"
---
# <a name="setsecurity-function"></a><span data-ttu-id="bf430-103">Função setsecurity</span><span class="sxs-lookup"><span data-stu-id="bf430-103">SetSecurity function</span></span>

<span data-ttu-id="bf430-104">Recupera o token de representação associado ao thread atual.</span><span class="sxs-lookup"><span data-stu-id="bf430-104">Retrieves the impersonation token associated with the current thread.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="bf430-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bf430-105">Syntax</span></span>

```cpp
HRESULT SetSecurity (
   [out] boolean* pNeedToReset, 
   [out] HANDLE* pCurrentThreadToken
); 
```

## <a name="parameters"></a><span data-ttu-id="bf430-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bf430-106">Parameters</span></span>

`pNeedToReset`\
<span data-ttu-id="bf430-107">fora Quando a função retorna, contém um ponteiro para um `boolean` que indica se o token deve ser redefinido chamando a função [ResetSecurity](resetsecurity.md) .</span><span class="sxs-lookup"><span data-stu-id="bf430-107">[out] When the function returns, contains a pointer to a `boolean` that indicates whether the token should be reset by calling the [ResetSecurity](resetsecurity.md) function.</span></span>

`token`\
<span data-ttu-id="bf430-108">fora Quando a função retorna, contém um ponteiro para o identificador do token de representação associado ao thread atual.</span><span class="sxs-lookup"><span data-stu-id="bf430-108">[out] When the function returns, contains a pointer to the handle of the impersonation token associated with the current thread.</span></span> <span data-ttu-id="bf430-109">Seu valor pode ser `null` se não houver nenhum token associado ao thread atual.</span><span class="sxs-lookup"><span data-stu-id="bf430-109">Its value can be `null` if there is no token associated with the current thread.</span></span> 

## <a name="return-value"></a><span data-ttu-id="bf430-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="bf430-110">Return value</span></span>

<span data-ttu-id="bf430-111">Se a função for realizada com sucesso, o valor `S_OK` de retorno será (0).</span><span class="sxs-lookup"><span data-stu-id="bf430-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="bf430-112">Se a função falhar, o valor de retorno será um código de erro diferente de zero.</span><span class="sxs-lookup"><span data-stu-id="bf430-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="bf430-113">Para obter informações de erro estendidas, chame a função [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="bf430-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="bf430-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bf430-114">Requirements</span></span>

 <span data-ttu-id="bf430-115">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf430-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="bf430-116">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="bf430-116">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="bf430-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bf430-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="bf430-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf430-118">See also</span></span>

- [<span data-ttu-id="bf430-119">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="bf430-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
