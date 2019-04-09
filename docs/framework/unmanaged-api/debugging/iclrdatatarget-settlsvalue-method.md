---
title: Método ICLRDataTarget::SetTLSValue
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.SetTLSValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::SetTLSValue
helpviewer_keywords:
- ICLRDataTarget::SetTLSValue method [.NET Framework debugging]
- SetTLSValue method [.NET Framework debugging]
ms.assetid: 4a2d6a24-749a-47ad-9f01-4517203d3f35
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c0be35772b10d89f90da5b33f47aa781034b13a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59152926"
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="95d4d-102">Método ICLRDataTarget::SetTLSValue</span><span class="sxs-lookup"><span data-stu-id="95d4d-102">ICLRDataTarget::SetTLSValue Method</span></span>
<span data-ttu-id="95d4d-103">Define um valor no armazenamento local de thread (TLS) do thread no processo de destino especificado.</span><span class="sxs-lookup"><span data-stu-id="95d4d-103">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="95d4d-104">Esse método é chamado pelo serviço de acesso de dados do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="95d4d-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95d4d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="95d4d-105">Syntax</span></span>  
  
```  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95d4d-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="95d4d-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="95d4d-107">[in] O identificador de sistema operacional de um thread no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="95d4d-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="95d4d-108">[in] O índice do local.</span><span class="sxs-lookup"><span data-stu-id="95d4d-108">[in] The index of the location.</span></span> <span data-ttu-id="95d4d-109">Esse valor deve ser um índice válido no repositório local do thread especificado.</span><span class="sxs-lookup"><span data-stu-id="95d4d-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="95d4d-110">[in] Um `CLRDATA_ADDRESS` valor que especifica o valor a ser colocado no local determinado TLS.</span><span class="sxs-lookup"><span data-stu-id="95d4d-110">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95d4d-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="95d4d-111">Remarks</span></span>  
 <span data-ttu-id="95d4d-112">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="95d4d-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95d4d-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="95d4d-113">Requirements</span></span>  
 <span data-ttu-id="95d4d-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95d4d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95d4d-115">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="95d4d-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="95d4d-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95d4d-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="95d4d-117">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="95d4d-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="95d4d-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95d4d-118">See also</span></span>

- [<span data-ttu-id="95d4d-119">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="95d4d-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
