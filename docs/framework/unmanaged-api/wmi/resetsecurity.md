---
title: Função ResetSecurity (referência de API não gerenciada)
description: A função ResetSecurity atribui um token de representação ao segmento atual.
ms.date: 11/06/2017
api_name:
- ResetSecurity
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ResetSecurity
helpviewer_keywords:
- ResetSecurity function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: ce74494455c6cc7fe382a4ea4ef2ff0c4e98c61b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174856"
---
# <a name="resetsecurity-function"></a><span data-ttu-id="f0031-103">Função ResetSecurity</span><span class="sxs-lookup"><span data-stu-id="f0031-103">ResetSecurity function</span></span>
<span data-ttu-id="f0031-104">Atribui o token de representação fornecido para o thread atual.</span><span class="sxs-lookup"><span data-stu-id="f0031-104">Assigns the supplied impersonation token to the current thread.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="f0031-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f0031-105">Syntax</span></span>  
  
```cpp  
HRESULT ResetSecurity (
   [in] HANDLE token
);
```  

## <a name="parameters"></a><span data-ttu-id="f0031-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="f0031-106">Parameters</span></span>

`token`  
<span data-ttu-id="f0031-107">[em] O token de representação para associar com o segmento atual.</span><span class="sxs-lookup"><span data-stu-id="f0031-107">[in] The impersonation token to associate with the current thread.</span></span> <span data-ttu-id="f0031-108">Seu valor pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="f0031-108">Its value can be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="f0031-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="f0031-109">Return value</span></span>

<span data-ttu-id="f0031-110">Se a função for bem `S_OK` sucedida, o valor de retorno será (0).</span><span class="sxs-lookup"><span data-stu-id="f0031-110">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="f0031-111">Se a função falhar, o valor de retorno será um código de erro não-zero.</span><span class="sxs-lookup"><span data-stu-id="f0031-111">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="f0031-112">Para obter informações de erro estendidas, ligue para a função [GetErrorInfo.](geterrorinfo.md)</span><span class="sxs-lookup"><span data-stu-id="f0031-112">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="f0031-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f0031-113">Requirements</span></span>  
 <span data-ttu-id="f0031-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0031-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0031-115">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f0031-115">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f0031-116">**.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f0031-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0031-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="f0031-117">See also</span></span>

- [<span data-ttu-id="f0031-118">WMI e Contadores de Desempenho (Referência de API Não Gerenciada)</span><span class="sxs-lookup"><span data-stu-id="f0031-118">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
