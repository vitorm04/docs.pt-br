---
title: Método ICLRDataTarget::Request
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.Request
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::Request
helpviewer_keywords:
- ICLRDataTarget::Request method [.NET Framework debugging]
- Request method [.NET Framework debugging]
ms.assetid: 4723bd1c-eddb-4ed2-897a-010024a47e01
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5f6926d66a438cfc4fd97d7120e359b737212dde
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738622"
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="70696-102">Método ICLRDataTarget::Request</span><span class="sxs-lookup"><span data-stu-id="70696-102">ICLRDataTarget::Request Method</span></span>
<span data-ttu-id="70696-103">Chamado pelo serviço common language runtime (CLR) dados acesso para solicitar uma operação, conforme definido pela implementação.</span><span class="sxs-lookup"><span data-stu-id="70696-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70696-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="70696-104">Syntax</span></span>  
  
```cpp  
HRESULT Request (  
    [in] ULONG32            reqCode,  
    [in] ULONG32            inBufferSize,  
    [in, size_is(inBufferSize)]   
        BYTE                *inBuffer,  
    [in] ULONG32            outBufferSize,  
    [out, size_is(outBufferSize)]   
        BYTE                *outBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70696-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="70696-105">Parameters</span></span>  
 `reqCode`  
 <span data-ttu-id="70696-106">[in] Definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="70696-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="70696-107">[in] O tamanho do buffer de entrada, que é usado para a solicitação de entrada.</span><span class="sxs-lookup"><span data-stu-id="70696-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="70696-108">[in] Um buffer que contém a solicitação.</span><span class="sxs-lookup"><span data-stu-id="70696-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="70696-109">[in] O tamanho do buffer de saída, que é usado para a resposta.</span><span class="sxs-lookup"><span data-stu-id="70696-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="70696-110">[out] Um Buffer que contém a resposta.</span><span class="sxs-lookup"><span data-stu-id="70696-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70696-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="70696-111">Remarks</span></span>  
 <span data-ttu-id="70696-112">O `Request` método facilita a adição de operações personalizadas não especificadas.</span><span class="sxs-lookup"><span data-stu-id="70696-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="70696-113">Ou seja, esse método fornece extensibilidade sem a necessidade de revisão da definição da interface.</span><span class="sxs-lookup"><span data-stu-id="70696-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="70696-114">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="70696-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70696-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="70696-115">Requirements</span></span>  
 <span data-ttu-id="70696-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70696-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70696-117">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="70696-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="70696-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70696-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70696-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70696-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70696-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70696-120">See also</span></span>

- [<span data-ttu-id="70696-121">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="70696-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
