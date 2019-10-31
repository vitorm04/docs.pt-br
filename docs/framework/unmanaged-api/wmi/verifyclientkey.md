---
title: Função VerifyClientKey (referência de API não gerenciada)
description: A função VerifyClientKey garante que a chave do cliente tenha a segurança correta.
ms.date: 11/06/2017
api_name:
- VerifyClientKey
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- VerifyClientKey
helpviewer_keywords:
- VerifyClientKey function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 0a0680651eb192e2798ede00048599c5130e63f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107358"
---
# <a name="verifyclientkey-function"></a><span data-ttu-id="359cd-103">Função VerifyClientKey</span><span class="sxs-lookup"><span data-stu-id="359cd-103">VerifyClientKey function</span></span>
<span data-ttu-id="359cd-104">Garante que a chave do cliente tenha a segurança correta.</span><span class="sxs-lookup"><span data-stu-id="359cd-104">Ensures that the client key has the correct security.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="359cd-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="359cd-105">Syntax</span></span>  
  
```cpp  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a><span data-ttu-id="359cd-106">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="359cd-106">Return value</span></span>

<span data-ttu-id="359cd-107">Se a função for realizada com sucesso, o valor de retorno será `ERROR_SUCCESS` (0).</span><span class="sxs-lookup"><span data-stu-id="359cd-107">If the function succeeds, the return value is `ERROR_SUCCESS` (0).</span></span>

<span data-ttu-id="359cd-108">Se a função falhar, o valor de retorno será um código de erro diferente de zero definido em *Winerror. h*.</span><span class="sxs-lookup"><span data-stu-id="359cd-108">If the function fails, the return value is a non-zero error code defined in *WinError.h*.</span></span>

## <a name="requirements"></a><span data-ttu-id="359cd-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="359cd-109">Requirements</span></span>  
 <span data-ttu-id="359cd-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="359cd-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="359cd-111">**Cabeçalho:** WMINet_Utils. def</span><span class="sxs-lookup"><span data-stu-id="359cd-111">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="359cd-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="359cd-112">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="359cd-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="359cd-113">See also</span></span>

- [<span data-ttu-id="359cd-114">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="359cd-114">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
