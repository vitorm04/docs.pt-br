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
ms.openlocfilehash: e5d7a6b9826a734363d6beeb2e3fab8422964558
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73113351"
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="931b4-102">Método ICLRDataTarget::Request</span><span class="sxs-lookup"><span data-stu-id="931b4-102">ICLRDataTarget::Request Method</span></span>
<span data-ttu-id="931b4-103">Chamado pelos serviços de acesso a dados do Common Language Runtime (CLR) para solicitar uma operação, conforme definido pela implementação.</span><span class="sxs-lookup"><span data-stu-id="931b4-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="931b4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="931b4-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="931b4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="931b4-105">Parameters</span></span>  
 `reqCode`  
 <span data-ttu-id="931b4-106">no Definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="931b4-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="931b4-107">no O tamanho do buffer de entrada, que é usado para a solicitação de entrada.</span><span class="sxs-lookup"><span data-stu-id="931b4-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="931b4-108">no Um buffer que contém a solicitação.</span><span class="sxs-lookup"><span data-stu-id="931b4-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="931b4-109">no O tamanho do buffer de saída, que é usado para a resposta.</span><span class="sxs-lookup"><span data-stu-id="931b4-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="931b4-110">fora Um buffer que contém a resposta.</span><span class="sxs-lookup"><span data-stu-id="931b4-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="931b4-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="931b4-111">Remarks</span></span>  
 <span data-ttu-id="931b4-112">O método `Request` facilita a adição de operações personalizadas não especificadas.</span><span class="sxs-lookup"><span data-stu-id="931b4-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="931b4-113">Ou seja, esse método fornece extensibilidade sem exigir a revisão da definição da interface.</span><span class="sxs-lookup"><span data-stu-id="931b4-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="931b4-114">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="931b4-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="931b4-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="931b4-115">Requirements</span></span>  
 <span data-ttu-id="931b4-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="931b4-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="931b4-117">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="931b4-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="931b4-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="931b4-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="931b4-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="931b4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="931b4-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="931b4-120">See also</span></span>

- [<span data-ttu-id="931b4-121">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="931b4-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
