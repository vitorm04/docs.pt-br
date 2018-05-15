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
ms.openlocfilehash: dc79277c75118b11766e66137284bd5655eed091
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="e6f7c-102">Método ICLRDataTarget::Request</span><span class="sxs-lookup"><span data-stu-id="e6f7c-102">ICLRDataTarget::Request Method</span></span>
<span data-ttu-id="e6f7c-103">Chamado pelos comuns language runtime (CLR) dados serviços de acesso para uma operação de solicitação, conforme definido pela implementação.</span><span class="sxs-lookup"><span data-stu-id="e6f7c-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6f7c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e6f7c-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="e6f7c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e6f7c-105">Parameters</span></span>  
 `reqCode`  
 <span data-ttu-id="e6f7c-106">[in] Definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="e6f7c-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="e6f7c-107">[in] O tamanho do buffer de entrada, que é usado para a solicitação de entrada.</span><span class="sxs-lookup"><span data-stu-id="e6f7c-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="e6f7c-108">[in] Um buffer que contém a solicitação.</span><span class="sxs-lookup"><span data-stu-id="e6f7c-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="e6f7c-109">[in] O tamanho do buffer de saída, que é usado para a resposta.</span><span class="sxs-lookup"><span data-stu-id="e6f7c-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="e6f7c-110">[out] Um Buffer que contém a resposta.</span><span class="sxs-lookup"><span data-stu-id="e6f7c-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6f7c-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="e6f7c-111">Remarks</span></span>  
 <span data-ttu-id="e6f7c-112">O `Request` método facilita a adição de operações personalizadas não especificadas.</span><span class="sxs-lookup"><span data-stu-id="e6f7c-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="e6f7c-113">Ou seja, esse método fornece extensibilidade sem a necessidade de revisão da definição da interface.</span><span class="sxs-lookup"><span data-stu-id="e6f7c-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="e6f7c-114">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="e6f7c-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6f7c-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e6f7c-115">Requirements</span></span>  
 <span data-ttu-id="e6f7c-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6f7c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6f7c-117">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="e6f7c-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="e6f7c-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6f7c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6f7c-119">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6f7c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6f7c-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6f7c-120">See Also</span></span>  
 [<span data-ttu-id="e6f7c-121">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="e6f7c-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
