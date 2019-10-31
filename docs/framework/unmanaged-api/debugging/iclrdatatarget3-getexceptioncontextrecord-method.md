---
title: ICLRDataTarget3::Método GetExceptionContextRecord
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetContextRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 66076ed5-f05c-4114-9788-94cb143abb8a
topic_type:
- apiref
ms.openlocfilehash: 5a090b7c4801e6b2baf56f1d80e7e52f2aaa9293
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73112296"
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a><span data-ttu-id="5f03f-102">ICLRDataTarget3::Método GetExceptionContextRecord</span><span class="sxs-lookup"><span data-stu-id="5f03f-102">ICLRDataTarget3::GetExceptionContextRecord Method</span></span>
<span data-ttu-id="5f03f-103">Chamado pelo serviço de acesso a dados do CLR (Common Language Runtime) para recuperar o registro de contexto associado ao processo de destino.</span><span class="sxs-lookup"><span data-stu-id="5f03f-103">Called by the common language runtime (CLR) data access services to retrieve the context record associated with the target process.</span></span> <span data-ttu-id="5f03f-104">Por exemplo, para um destino de despejo, isso seria equivalente ao registro de contexto passado por meio do argumento `ExceptionParam` para a função [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) na biblioteca de ajuda de depuração do Windows (dbghelp).</span><span class="sxs-lookup"><span data-stu-id="5f03f-104">For example, for a dump target, this would be equivalent to the context record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f03f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5f03f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f03f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5f03f-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="5f03f-107">[in] O tamanho do buffer de entrada, em bytes.</span><span class="sxs-lookup"><span data-stu-id="5f03f-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="5f03f-108">Deve ser grande o suficiente para acomodar o registro de contexto.</span><span class="sxs-lookup"><span data-stu-id="5f03f-108">This must be large enough to accommodate the context record.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="5f03f-109">[out] Um ponteiro para um tipo `ULONG32` que recebe o número de bytes realmente gravados no buffer.</span><span class="sxs-lookup"><span data-stu-id="5f03f-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="5f03f-110">[out] Um ponteiro para um buffer de memória que recebe uma cópia do registro de contexto.</span><span class="sxs-lookup"><span data-stu-id="5f03f-110">[out] A pointer to a memory buffer that receives a copy of the context record.</span></span> <span data-ttu-id="5f03f-111">O registro de exceção é retornado como um tipo de [contexto](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) .</span><span class="sxs-lookup"><span data-stu-id="5f03f-111">The exception record is returned as a [CONTEXT](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5f03f-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="5f03f-112">Return Value</span></span>  
 <span data-ttu-id="5f03f-113">O valor retornado é `S_OK` em caso de êxito, ou um código de falha `HRESULT` em caso de falha.</span><span class="sxs-lookup"><span data-stu-id="5f03f-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="5f03f-114">Os códigos `HRESULT` podem incluir, entre outros:</span><span class="sxs-lookup"><span data-stu-id="5f03f-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="5f03f-115">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="5f03f-115">Return code</span></span>|<span data-ttu-id="5f03f-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="5f03f-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="5f03f-117">O método foi bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="5f03f-117">Method succeeded.</span></span> <span data-ttu-id="5f03f-118">O registro de contexto foi copiado no buffer de saída.</span><span class="sxs-lookup"><span data-stu-id="5f03f-118">The context record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="5f03f-119">Nenhum registro de contexto está associado ao destino.</span><span class="sxs-lookup"><span data-stu-id="5f03f-119">No context record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="5f03f-120">O tamanho do buffer de entrada não é grande o suficiente para acomodar o registro de contexto.</span><span class="sxs-lookup"><span data-stu-id="5f03f-120">The input buffer size is not large enough to accommodate the context record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f03f-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="5f03f-121">Remarks</span></span>  
 <span data-ttu-id="5f03f-122">O [contexto](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) é uma estrutura específica da plataforma definida nos cabeçalhos fornecidos pelo SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="5f03f-122">[CONTEXT](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) is a platform-specific structure defined in headers provided by the Windows SDK.</span></span>  
  
 <span data-ttu-id="5f03f-123">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="5f03f-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f03f-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5f03f-124">Requirements</span></span>  
 <span data-ttu-id="5f03f-125">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f03f-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f03f-126">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="5f03f-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="5f03f-127">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f03f-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f03f-128">**Versões do .NET Framework:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5f03f-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f03f-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5f03f-129">See also</span></span>

- [<span data-ttu-id="5f03f-130">Interface ICLRDataTarget3</span><span class="sxs-lookup"><span data-stu-id="5f03f-130">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)
- [<span data-ttu-id="5f03f-131">Método GetExceptionRecord</span><span class="sxs-lookup"><span data-stu-id="5f03f-131">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)
- [<span data-ttu-id="5f03f-132">Método GetExceptionThreadID</span><span class="sxs-lookup"><span data-stu-id="5f03f-132">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
