---
title: Método ICLRDataTarget::GetTLSValue
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetTLSValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetTLSValue
helpviewer_keywords:
- GetTLSValue method [.NET Framework debugging]
- ICLRDataTarget::GetTLSValue method [.NET Framework debugging]
ms.assetid: 0d8a7730-edc9-4728-898f-41b219cf5a28
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21fa9a17067f754fe9b13c4d32193856a57750ca
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227360"
---
# <a name="iclrdatatargetgettlsvalue-method"></a><span data-ttu-id="e39d7-102">Método ICLRDataTarget::GetTLSValue</span><span class="sxs-lookup"><span data-stu-id="e39d7-102">ICLRDataTarget::GetTLSValue Method</span></span>
<span data-ttu-id="e39d7-103">Obtém um valor de armazenamento local de thread (TLS) do thread no processo de destino especificado.</span><span class="sxs-lookup"><span data-stu-id="e39d7-103">Gets a value from the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="e39d7-104">Esse método é chamado pelo serviço de acesso de dados do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="e39d7-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e39d7-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e39d7-105">Syntax</span></span>  
  
```  
HRESULT GetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [out] CLRDATA_ADDRESS   *value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e39d7-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e39d7-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="e39d7-107">[in] O identificador de sistema operacional de um thread no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="e39d7-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="e39d7-108">[in] O índice do local.</span><span class="sxs-lookup"><span data-stu-id="e39d7-108">[in] The index of the location.</span></span> <span data-ttu-id="e39d7-109">Esse valor deve ser um índice válido no repositório local do thread especificado.</span><span class="sxs-lookup"><span data-stu-id="e39d7-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="e39d7-110">[out] Um ponteiro para um `CLRDATA_ADDRESS` valor que especifica o valor retornado do local indicado TLS.</span><span class="sxs-lookup"><span data-stu-id="e39d7-110">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the value returned from the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e39d7-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="e39d7-111">Remarks</span></span>  
 <span data-ttu-id="e39d7-112">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="e39d7-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e39d7-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e39d7-113">Requirements</span></span>  
 <span data-ttu-id="e39d7-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e39d7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e39d7-115">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="e39d7-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="e39d7-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e39d7-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e39d7-117">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="e39d7-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e39d7-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e39d7-118">See also</span></span>

- [<span data-ttu-id="e39d7-119">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="e39d7-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
