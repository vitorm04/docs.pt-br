---
title: Função GetDemultiplexedStub (referência de API não gerenciada)
description: A função GetDemultiplexedStub cria um coletor do encaminhador de objeto para ajudar um cliente receber chamadas assíncronas de gerenciamento do Windows.
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
ms.openlocfilehash: 872164e2f48f1ef234b729b28aa9b1af1589c0fc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180929"
---
# <a name="getdemultiplexedstub-function"></a><span data-ttu-id="0be8c-103">Função GetDemultiplexedStub</span><span class="sxs-lookup"><span data-stu-id="0be8c-103">GetDemultiplexedStub function</span></span>
<span data-ttu-id="0be8c-104">Cria um coletor do encaminhador de objeto para ajudar um cliente a receber chamadas assíncronas do Gerenciamento do Windows.</span><span class="sxs-lookup"><span data-stu-id="0be8c-104">Creates an object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="0be8c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0be8c-105">Syntax</span></span>  
  
```  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject, 
   [in] boolean      isLocal, 
   [out] IUnknown**  ppObject
); 
```  

## <a name="parameters"></a><span data-ttu-id="0be8c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0be8c-106">Parameters</span></span>

`pObject`  
<span data-ttu-id="0be8c-107">[in] Um ponteiro para a implementação em processo do cliente do [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).</span><span class="sxs-lookup"><span data-stu-id="0be8c-107">[in] A pointer to the client's in-process implementation of [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).</span></span>

`isLocal`  
<span data-ttu-id="0be8c-108">[in] Um sinalizador que indica se o evento é local (`true`); caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="0be8c-108">[in] A flag that indicates whether the event is local (`true`); otherwise, `false`.</span></span>

`ppObject`  
<span data-ttu-id="0be8c-109">[out] Um coletor do encaminhador de objeto para ajudar um cliente receber chamadas assíncronas de gerenciamento do Windows.</span><span class="sxs-lookup"><span data-stu-id="0be8c-109">[out] A object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>

## <a name="return-value"></a><span data-ttu-id="0be8c-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="0be8c-110">Return value</span></span>

<span data-ttu-id="0be8c-111">Se a função for bem-sucedida, o valor retornado é `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="0be8c-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="0be8c-112">Se a função falhar, o valor de retorno é um código de erro diferente de zero.</span><span class="sxs-lookup"><span data-stu-id="0be8c-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="0be8c-113">Para obter outras informações de erro, chame o [GetErrorInfo](geterrorinfo.md) função.</span><span class="sxs-lookup"><span data-stu-id="0be8c-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
    
## <a name="requirements"></a><span data-ttu-id="0be8c-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0be8c-114">Requirements</span></span>  
 <span data-ttu-id="0be8c-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0be8c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0be8c-116">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="0be8c-116">**Header:** WMINet_Utils.idl</span></span>  
  
 **<span data-ttu-id="0be8c-117">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="0be8c-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0be8c-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0be8c-118">See also</span></span>

- [<span data-ttu-id="0be8c-119">WMI e Contadores de Desempenho (Referência de API Não Gerenciada)</span><span class="sxs-lookup"><span data-stu-id="0be8c-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
