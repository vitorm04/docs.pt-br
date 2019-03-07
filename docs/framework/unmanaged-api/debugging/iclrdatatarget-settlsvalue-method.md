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
ms.openlocfilehash: 421fb371094c21948486e56d0881163e7a6961a0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465277"
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="da488-102">Método ICLRDataTarget::SetTLSValue</span><span class="sxs-lookup"><span data-stu-id="da488-102">ICLRDataTarget::SetTLSValue Method</span></span>
<span data-ttu-id="da488-103">Define um valor no armazenamento local de thread (TLS) do thread no processo de destino especificado.</span><span class="sxs-lookup"><span data-stu-id="da488-103">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="da488-104">Esse método é chamado pelo serviço de acesso de dados do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="da488-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da488-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="da488-105">Syntax</span></span>  
  
```  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da488-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="da488-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="da488-107">[in] O identificador de sistema operacional de um thread no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="da488-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="da488-108">[in] O índice do local.</span><span class="sxs-lookup"><span data-stu-id="da488-108">[in] The index of the location.</span></span> <span data-ttu-id="da488-109">Esse valor deve ser um índice válido no repositório local do thread especificado.</span><span class="sxs-lookup"><span data-stu-id="da488-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="da488-110">[in] Um `CLRDATA_ADDRESS` valor que especifica o valor a ser colocado no local determinado TLS.</span><span class="sxs-lookup"><span data-stu-id="da488-110">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da488-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="da488-111">Remarks</span></span>  
 <span data-ttu-id="da488-112">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="da488-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da488-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="da488-113">Requirements</span></span>  
 <span data-ttu-id="da488-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da488-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da488-115">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="da488-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="da488-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da488-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da488-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da488-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da488-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="da488-118">See also</span></span>
- [<span data-ttu-id="da488-119">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="da488-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
