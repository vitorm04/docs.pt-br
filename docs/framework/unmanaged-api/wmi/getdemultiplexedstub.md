---
title: Função GetDemultiplexedStub (referência de API não gerenciada)
description: A função GetDemultiplexedStub cria um coletor de encaminhador de objetos para ajudar um cliente a receber chamadas assíncronas do gerenciamento do Windows.
ms.date: 11/06/2017
api_name:
- GetDemultiplexedStub
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetDemultiplexedStub
helpviewer_keywords:
- GetDemultiplexedStub function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a2d3885a4a9e54950909053ba18de5b1891e7edf
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798601"
---
# <a name="getdemultiplexedstub-function"></a><span data-ttu-id="cd2cc-103">Função GetDemultiplexedStub</span><span class="sxs-lookup"><span data-stu-id="cd2cc-103">GetDemultiplexedStub function</span></span>
<span data-ttu-id="cd2cc-104">Cria um coletor do encaminhador de objeto para ajudar um cliente a receber chamadas assíncronas do Gerenciamento do Windows.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-104">Creates an object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="cd2cc-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cd2cc-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject, 
   [in] boolean      isLocal, 
   [out] IUnknown**  ppObject
); 
```  

## <a name="parameters"></a><span data-ttu-id="cd2cc-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cd2cc-106">Parameters</span></span>

`pObject`  
<span data-ttu-id="cd2cc-107">no Um ponteiro para a implementação em processo do cliente do [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).</span><span class="sxs-lookup"><span data-stu-id="cd2cc-107">[in] A pointer to the client's in-process implementation of [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).</span></span>

`isLocal`  
<span data-ttu-id="cd2cc-108">no Um sinalizador que indica se o evento é local (`true`); caso contrário `false`,.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-108">[in] A flag that indicates whether the event is local (`true`); otherwise, `false`.</span></span>

`ppObject`  
<span data-ttu-id="cd2cc-109">fora Um coletor de encaminhador de objetos para auxiliar um cliente no recebimento de chamadas assíncronas do gerenciamento do Windows.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-109">[out] A object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>

## <a name="return-value"></a><span data-ttu-id="cd2cc-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="cd2cc-110">Return value</span></span>

<span data-ttu-id="cd2cc-111">Se a função for realizada com sucesso, o valor `S_OK` de retorno será (0).</span><span class="sxs-lookup"><span data-stu-id="cd2cc-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="cd2cc-112">Se a função falhar, o valor de retorno será um código de erro diferente de zero.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="cd2cc-113">Para obter informações de erro estendidas, chame a função [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="cd2cc-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
    
## <a name="requirements"></a><span data-ttu-id="cd2cc-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cd2cc-114">Requirements</span></span>  
 <span data-ttu-id="cd2cc-115">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd2cc-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd2cc-116">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="cd2cc-116">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="cd2cc-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="cd2cc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd2cc-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cd2cc-118">See also</span></span>

- [<span data-ttu-id="cd2cc-119">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="cd2cc-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
