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
ms.openlocfilehash: 6e6e157c7176a0f4f1ad3c585977e2cfb31c33d8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793683"
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="b63a6-102">Método ICLRDataTarget::SetTLSValue</span><span class="sxs-lookup"><span data-stu-id="b63a6-102">ICLRDataTarget::SetTLSValue Method</span></span>
<span data-ttu-id="b63a6-103">Define um valor no armazenamento local de threads (TLS) do thread especificado no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="b63a6-103">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="b63a6-104">Esse método é chamado pelos serviços de acesso a dados do Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="b63a6-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b63a6-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b63a6-105">Syntax</span></span>  
  
```cpp  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b63a6-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b63a6-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="b63a6-107">no O identificador do sistema operacional de um thread no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="b63a6-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="b63a6-108">no O índice do local.</span><span class="sxs-lookup"><span data-stu-id="b63a6-108">[in] The index of the location.</span></span> <span data-ttu-id="b63a6-109">Esse valor deve ser um índice válido no repositório local do thread especificado.</span><span class="sxs-lookup"><span data-stu-id="b63a6-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="b63a6-110">no Um valor `CLRDATA_ADDRESS` que especifica o valor a ser colocado no local de TLS fornecido.</span><span class="sxs-lookup"><span data-stu-id="b63a6-110">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b63a6-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="b63a6-111">Remarks</span></span>  
 <span data-ttu-id="b63a6-112">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="b63a6-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b63a6-113">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="b63a6-113">Requirements</span></span>  
 <span data-ttu-id="b63a6-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b63a6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b63a6-115">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="b63a6-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="b63a6-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b63a6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b63a6-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b63a6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b63a6-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="b63a6-118">See also</span></span>

- [<span data-ttu-id="b63a6-119">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="b63a6-119">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
