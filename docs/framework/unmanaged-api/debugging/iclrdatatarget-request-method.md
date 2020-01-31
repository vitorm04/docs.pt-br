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
ms.openlocfilehash: 0a7e764d89dd42bcaf81da5cf6a16991b6b8a16e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793700"
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="180dd-102">Método ICLRDataTarget::Request</span><span class="sxs-lookup"><span data-stu-id="180dd-102">ICLRDataTarget::Request Method</span></span>
<span data-ttu-id="180dd-103">Chamado pelos serviços de acesso a dados do Common Language Runtime (CLR) para solicitar uma operação, conforme definido pela implementação.</span><span class="sxs-lookup"><span data-stu-id="180dd-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="180dd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="180dd-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="180dd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="180dd-105">Parameters</span></span>  
 `reqCode`  
 <span data-ttu-id="180dd-106">no Definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="180dd-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="180dd-107">no O tamanho do buffer de entrada, que é usado para a solicitação de entrada.</span><span class="sxs-lookup"><span data-stu-id="180dd-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="180dd-108">no Um buffer que contém a solicitação.</span><span class="sxs-lookup"><span data-stu-id="180dd-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="180dd-109">no O tamanho do buffer de saída, que é usado para a resposta.</span><span class="sxs-lookup"><span data-stu-id="180dd-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="180dd-110">fora Um buffer que contém a resposta.</span><span class="sxs-lookup"><span data-stu-id="180dd-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="180dd-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="180dd-111">Remarks</span></span>  
 <span data-ttu-id="180dd-112">O método `Request` facilita a adição de operações personalizadas não especificadas.</span><span class="sxs-lookup"><span data-stu-id="180dd-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="180dd-113">Ou seja, esse método fornece extensibilidade sem exigir a revisão da definição da interface.</span><span class="sxs-lookup"><span data-stu-id="180dd-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="180dd-114">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="180dd-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="180dd-115">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="180dd-115">Requirements</span></span>  
 <span data-ttu-id="180dd-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="180dd-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="180dd-117">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="180dd-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="180dd-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="180dd-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="180dd-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="180dd-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="180dd-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="180dd-120">See also</span></span>

- [<span data-ttu-id="180dd-121">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="180dd-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
