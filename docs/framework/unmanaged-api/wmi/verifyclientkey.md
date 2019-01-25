---
title: Função VerifyClientKey (referência de API não gerenciada)
description: A função VerifyClientKey garante que a chave do cliente tem a segurança correta.
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
ms.openlocfilehash: 94d601125049f0c215b3b03bf8b13d2959872c3d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54711753"
---
# <a name="verifyclientkey-function"></a><span data-ttu-id="5e1c7-103">Função VerifyClientKey</span><span class="sxs-lookup"><span data-stu-id="5e1c7-103">VerifyClientKey function</span></span>
<span data-ttu-id="5e1c7-104">Garante que a chave do cliente tenha a segurança correta.</span><span class="sxs-lookup"><span data-stu-id="5e1c7-104">Ensures that the client key has the correct security.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="5e1c7-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5e1c7-105">Syntax</span></span>  
  
```  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a><span data-ttu-id="5e1c7-106">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="5e1c7-106">Return value</span></span>

<span data-ttu-id="5e1c7-107">Se a função for bem-sucedida, o valor retornado é `ERROR_SUCCESS` (0).</span><span class="sxs-lookup"><span data-stu-id="5e1c7-107">If the function succeeds, the return value is `ERROR_SUCCESS` (0).</span></span>

<span data-ttu-id="5e1c7-108">Se a função falhar, o valor retornado é um código de erro diferente de zero definido na *Winerror. H*.</span><span class="sxs-lookup"><span data-stu-id="5e1c7-108">If the function fails, the return value is a non-zero error code defined in *WinError.h*.</span></span>

## <a name="requirements"></a><span data-ttu-id="5e1c7-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5e1c7-109">Requirements</span></span>  
 <span data-ttu-id="5e1c7-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e1c7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e1c7-111">**Cabeçalho:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="5e1c7-111">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="5e1c7-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5e1c7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e1c7-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e1c7-113">See also</span></span>
- [<span data-ttu-id="5e1c7-114">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="5e1c7-114">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
