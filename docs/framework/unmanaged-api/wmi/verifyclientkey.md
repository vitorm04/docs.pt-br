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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b674e959ab93cf76b84e2af41e875a50b7d115f4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798197"
---
# <a name="verifyclientkey-function"></a><span data-ttu-id="f950f-103">Função VerifyClientKey</span><span class="sxs-lookup"><span data-stu-id="f950f-103">VerifyClientKey function</span></span>
<span data-ttu-id="f950f-104">Garante que a chave do cliente tenha a segurança correta.</span><span class="sxs-lookup"><span data-stu-id="f950f-104">Ensures that the client key has the correct security.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="f950f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f950f-105">Syntax</span></span>  
  
```cpp  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a><span data-ttu-id="f950f-106">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="f950f-106">Return value</span></span>

<span data-ttu-id="f950f-107">Se a função for realizada com sucesso, o valor `ERROR_SUCCESS` de retorno será (0).</span><span class="sxs-lookup"><span data-stu-id="f950f-107">If the function succeeds, the return value is `ERROR_SUCCESS` (0).</span></span>

<span data-ttu-id="f950f-108">Se a função falhar, o valor de retorno será um código de erro diferente de zero definido em *Winerror. h*.</span><span class="sxs-lookup"><span data-stu-id="f950f-108">If the function fails, the return value is a non-zero error code defined in *WinError.h*.</span></span>

## <a name="requirements"></a><span data-ttu-id="f950f-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f950f-109">Requirements</span></span>  
 <span data-ttu-id="f950f-110">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f950f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f950f-111">**Cabeçalho:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="f950f-111">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="f950f-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f950f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f950f-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f950f-113">See also</span></span>

- [<span data-ttu-id="f950f-114">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="f950f-114">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
