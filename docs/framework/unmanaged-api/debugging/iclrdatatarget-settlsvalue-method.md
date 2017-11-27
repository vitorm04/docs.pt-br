---
title: "Método ICLRDataTarget::SetTLSValue"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.SetTLSValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::SetTLSValue
helpviewer_keywords:
- ICLRDataTarget::SetTLSValue method [.NET Framework debugging]
- SetTLSValue method [.NET Framework debugging]
ms.assetid: 4a2d6a24-749a-47ad-9f01-4517203d3f35
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 75c9d25b496e300d66844e3fd88655ab38da4b0e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="b2ffb-102">Método ICLRDataTarget::SetTLSValue</span><span class="sxs-lookup"><span data-stu-id="b2ffb-102">ICLRDataTarget::SetTLSValue Method</span></span>
<span data-ttu-id="b2ffb-103">Define um valor no armazenamento local de thread (TLS) do thread no processo de destino especificado.</span><span class="sxs-lookup"><span data-stu-id="b2ffb-103">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="b2ffb-104">Este método é chamado, os serviços de acesso dados common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="b2ffb-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2ffb-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b2ffb-105">Syntax</span></span>  
  
```  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b2ffb-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b2ffb-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="b2ffb-107">[in] O identificador de sistema operacional de um thread no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="b2ffb-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="b2ffb-108">[in] O índice do local.</span><span class="sxs-lookup"><span data-stu-id="b2ffb-108">[in] The index of the location.</span></span> <span data-ttu-id="b2ffb-109">Esse valor deve ser um índice válido no repositório local de thread especificado.</span><span class="sxs-lookup"><span data-stu-id="b2ffb-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="b2ffb-110">[in] Um `CLRDATA_ADDRESS` valor que especifica o valor a ser colocado no local determinado TLS.</span><span class="sxs-lookup"><span data-stu-id="b2ffb-110">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2ffb-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="b2ffb-111">Remarks</span></span>  
 <span data-ttu-id="b2ffb-112">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="b2ffb-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2ffb-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b2ffb-113">Requirements</span></span>  
 <span data-ttu-id="b2ffb-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2ffb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2ffb-115">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="b2ffb-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="b2ffb-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2ffb-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2ffb-117">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2ffb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2ffb-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2ffb-118">See Also</span></span>  
 [<span data-ttu-id="b2ffb-119">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="b2ffb-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
