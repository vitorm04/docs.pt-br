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
ms.openlocfilehash: 5a3c1aad3bcd6151267671122fb21772082e15cd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658774"
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="f2449-102">Método ICLRDataTarget::SetTLSValue</span><span class="sxs-lookup"><span data-stu-id="f2449-102">ICLRDataTarget::SetTLSValue Method</span></span>
<span data-ttu-id="f2449-103">Define um valor no armazenamento local de thread (TLS) do thread no processo de destino especificado.</span><span class="sxs-lookup"><span data-stu-id="f2449-103">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="f2449-104">Esse método é chamado pelo serviço de acesso de dados do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="f2449-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2449-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f2449-105">Syntax</span></span>  
  
```  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f2449-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f2449-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="f2449-107">[in] O identificador de sistema operacional de um thread no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="f2449-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="f2449-108">[in] O índice do local.</span><span class="sxs-lookup"><span data-stu-id="f2449-108">[in] The index of the location.</span></span> <span data-ttu-id="f2449-109">Esse valor deve ser um índice válido no repositório local do thread especificado.</span><span class="sxs-lookup"><span data-stu-id="f2449-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="f2449-110">[in] Um `CLRDATA_ADDRESS` valor que especifica o valor a ser colocado no local determinado TLS.</span><span class="sxs-lookup"><span data-stu-id="f2449-110">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2449-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="f2449-111">Remarks</span></span>  
 <span data-ttu-id="f2449-112">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="f2449-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2449-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f2449-113">Requirements</span></span>  
 <span data-ttu-id="f2449-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2449-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2449-115">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="f2449-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="f2449-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2449-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2449-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2449-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2449-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2449-118">See also</span></span>
- [<span data-ttu-id="f2449-119">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="f2449-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
