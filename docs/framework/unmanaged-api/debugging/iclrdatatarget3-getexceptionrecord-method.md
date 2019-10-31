---
title: Método ICLRDataTarget3::GetExceptionRecord
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetExceptionRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6643c2af-2ee6-4789-aa25-1d8eaf500c94
topic_type:
- apiref
ms.openlocfilehash: d5e7841844c8fa500935eb9cba06f4e2fe95d2d5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111992"
---
# <a name="iclrdatatarget3getexceptionrecord-method"></a><span data-ttu-id="b2136-102">Método ICLRDataTarget3::GetExceptionRecord</span><span class="sxs-lookup"><span data-stu-id="b2136-102">ICLRDataTarget3::GetExceptionRecord Method</span></span>
<span data-ttu-id="b2136-103">Chamado pelo serviço de acesso a dados do CLR (Common Language Runtime) para recuperar o registro de exceção associado ao processo de destino.</span><span class="sxs-lookup"><span data-stu-id="b2136-103">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span> <span data-ttu-id="b2136-104">Por exemplo, para um destino de despejo, isso seria equivalente ao registro de exceção passado por meio do argumento `ExceptionParam` para a função [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) na biblioteca de ajuda de depuração do Windows (dbghelp).</span><span class="sxs-lookup"><span data-stu-id="b2136-104">For example, for a dump target, this would be equivalent to the exception record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2136-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b2136-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2136-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b2136-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="b2136-107">[in] O tamanho do buffer de entrada, em bytes.</span><span class="sxs-lookup"><span data-stu-id="b2136-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="b2136-108">Isso deve ser igual a `sizeof(`[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception)`)`.</span><span class="sxs-lookup"><span data-stu-id="b2136-108">This must be equal to `sizeof(`[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception)`)`.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="b2136-109">[out] Um ponteiro para um tipo `ULONG32` que recebe o número de bytes realmente gravados no buffer.</span><span class="sxs-lookup"><span data-stu-id="b2136-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="b2136-110">[out] Um ponteiro para um buffer de memória que recebe uma cópia do registro de exceção.</span><span class="sxs-lookup"><span data-stu-id="b2136-110">[out] A pointer to a memory buffer that receives a copy of the exception record.</span></span> <span data-ttu-id="b2136-111">O registro de exceção é retornado como um tipo [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) .</span><span class="sxs-lookup"><span data-stu-id="b2136-111">The exception record is returned as a [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2136-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b2136-112">Return Value</span></span>  
 <span data-ttu-id="b2136-113">O valor retornado é `S_OK` em caso de êxito, ou um código de falha `HRESULT` em caso de falha.</span><span class="sxs-lookup"><span data-stu-id="b2136-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="b2136-114">Os códigos `HRESULT` podem incluir, entre outros:</span><span class="sxs-lookup"><span data-stu-id="b2136-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="b2136-115">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="b2136-115">Return code</span></span>|<span data-ttu-id="b2136-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="b2136-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="b2136-117">O método foi bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="b2136-117">Method succeeded.</span></span> <span data-ttu-id="b2136-118">O registro de exceção foi copiado para o buffer de saída.</span><span class="sxs-lookup"><span data-stu-id="b2136-118">The exception record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="b2136-119">Nenhum registro de exceção está associado ao destino.</span><span class="sxs-lookup"><span data-stu-id="b2136-119">No exception record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="b2136-120">O tamanho do buffer de entrada não é igual à `sizeof(MINIDUMP_EXCEPTION)`.</span><span class="sxs-lookup"><span data-stu-id="b2136-120">The input buffer size is not equal to `sizeof(MINIDUMP_EXCEPTION)`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2136-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="b2136-121">Remarks</span></span>  
 <span data-ttu-id="b2136-122">[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) é uma estrutura definida em dbghelp. h e imagehlp. h no SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="b2136-122">[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) is a structure defined in dbghelp.h and imagehlp.h in the Windows SDK.</span></span>  
  
 <span data-ttu-id="b2136-123">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="b2136-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2136-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b2136-124">Requirements</span></span>  
 <span data-ttu-id="b2136-125">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2136-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2136-126">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="b2136-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="b2136-127">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2136-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2136-128">**Versões do .NET Framework:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b2136-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2136-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2136-129">See also</span></span>

- [<span data-ttu-id="b2136-130">Interface ICLRDataTarget3</span><span class="sxs-lookup"><span data-stu-id="b2136-130">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)
- [<span data-ttu-id="b2136-131">Método GetExceptionContextRecord</span><span class="sxs-lookup"><span data-stu-id="b2136-131">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)
- [<span data-ttu-id="b2136-132">Método GetExceptionThreadID</span><span class="sxs-lookup"><span data-stu-id="b2136-132">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
