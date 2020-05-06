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
ms.openlocfilehash: 6c98fc93fd659ccfc0ccd42eec7d95382cf342f8
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860516"
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="4faca-102">Método ICLRDataTarget::SetTLSValue</span><span class="sxs-lookup"><span data-stu-id="4faca-102">ICLRDataTarget::SetTLSValue Method</span></span>
<span data-ttu-id="4faca-103">Define um valor no armazenamento local de threads (TLS) do thread especificado no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="4faca-103">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="4faca-104">Esse método é chamado pelos serviços de acesso a dados do Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="4faca-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4faca-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4faca-105">Syntax</span></span>  
  
```cpp  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4faca-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4faca-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="4faca-107">no O identificador do sistema operacional de um thread no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="4faca-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="4faca-108">no O índice do local.</span><span class="sxs-lookup"><span data-stu-id="4faca-108">[in] The index of the location.</span></span> <span data-ttu-id="4faca-109">Esse valor deve ser um índice válido no repositório local do thread especificado.</span><span class="sxs-lookup"><span data-stu-id="4faca-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="4faca-110">no Um `CLRDATA_ADDRESS` valor que especifica o valor a ser colocado no local de TLS fornecido.</span><span class="sxs-lookup"><span data-stu-id="4faca-110">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4faca-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="4faca-111">Remarks</span></span>  
 <span data-ttu-id="4faca-112">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="4faca-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4faca-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4faca-113">Requirements</span></span>  
 <span data-ttu-id="4faca-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4faca-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4faca-115">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="4faca-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="4faca-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4faca-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4faca-117">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4faca-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4faca-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="4faca-118">See also</span></span>

- [<span data-ttu-id="4faca-119">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="4faca-119">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
