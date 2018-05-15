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
ms.openlocfilehash: 18733c2d643a75f9bb11159ba4acdbc8ab064c55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="cdd17-102">Método ICLRDataTarget::SetTLSValue</span><span class="sxs-lookup"><span data-stu-id="cdd17-102">ICLRDataTarget::SetTLSValue Method</span></span>
<span data-ttu-id="cdd17-103">Define um valor no armazenamento local de thread (TLS) do thread no processo de destino especificado.</span><span class="sxs-lookup"><span data-stu-id="cdd17-103">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="cdd17-104">Este método é chamado, os serviços de acesso dados common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="cdd17-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdd17-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cdd17-105">Syntax</span></span>  
  
```  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cdd17-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cdd17-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="cdd17-107">[in] O identificador de sistema operacional de um thread no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="cdd17-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="cdd17-108">[in] O índice do local.</span><span class="sxs-lookup"><span data-stu-id="cdd17-108">[in] The index of the location.</span></span> <span data-ttu-id="cdd17-109">Esse valor deve ser um índice válido no repositório local de thread especificado.</span><span class="sxs-lookup"><span data-stu-id="cdd17-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="cdd17-110">[in] Um `CLRDATA_ADDRESS` valor que especifica o valor a ser colocado no local determinado TLS.</span><span class="sxs-lookup"><span data-stu-id="cdd17-110">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cdd17-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="cdd17-111">Remarks</span></span>  
 <span data-ttu-id="cdd17-112">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="cdd17-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdd17-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cdd17-113">Requirements</span></span>  
 <span data-ttu-id="cdd17-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cdd17-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdd17-115">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="cdd17-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="cdd17-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cdd17-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cdd17-117">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdd17-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdd17-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cdd17-118">See Also</span></span>  
 [<span data-ttu-id="cdd17-119">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="cdd17-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
