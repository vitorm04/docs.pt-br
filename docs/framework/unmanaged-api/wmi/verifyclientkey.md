---
title: Verificar funçãoClientKey (referência de API não gerenciada)
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
ms.openlocfilehash: ebb794240494deb0c831b50e95461ec52017a215
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176702"
---
# <a name="verifyclientkey-function"></a><span data-ttu-id="60526-103">Verificar funçãoClientKey</span><span class="sxs-lookup"><span data-stu-id="60526-103">VerifyClientKey function</span></span>
<span data-ttu-id="60526-104">Garante que a chave do cliente tenha a segurança correta.</span><span class="sxs-lookup"><span data-stu-id="60526-104">Ensures that the client key has the correct security.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="60526-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="60526-105">Syntax</span></span>  
  
```cpp  
LONG VerifyClientKey();
```  

## <a name="return-value"></a><span data-ttu-id="60526-106">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="60526-106">Return value</span></span>

<span data-ttu-id="60526-107">Se a função for bem `ERROR_SUCCESS` sucedida, o valor de retorno será (0).</span><span class="sxs-lookup"><span data-stu-id="60526-107">If the function succeeds, the return value is `ERROR_SUCCESS` (0).</span></span>

<span data-ttu-id="60526-108">Se a função falhar, o valor de retorno será um código de erro não-zero definido em *WinError.h*.</span><span class="sxs-lookup"><span data-stu-id="60526-108">If the function fails, the return value is a non-zero error code defined in *WinError.h*.</span></span>

## <a name="requirements"></a><span data-ttu-id="60526-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="60526-109">Requirements</span></span>  
 <span data-ttu-id="60526-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60526-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60526-111">**Cabeçalho:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="60526-111">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="60526-112">**.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="60526-112">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60526-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="60526-113">See also</span></span>

- [<span data-ttu-id="60526-114">WMI e Contadores de Desempenho (Referência de API Não Gerenciada)</span><span class="sxs-lookup"><span data-stu-id="60526-114">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
