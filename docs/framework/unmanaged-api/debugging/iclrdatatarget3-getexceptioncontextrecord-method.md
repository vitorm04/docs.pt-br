---
title: "ICLRDataTarget3::Método GetExceptionContextRecord"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICLRDataTarget3.GetContextRecord
api_location: mscordbi.dll
api_type: COM
ms.assetid: 66076ed5-f05c-4114-9788-94cb143abb8a
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 517e2a692c3b67a85bc24437dd5fbaedd5fc7254
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a><span data-ttu-id="95010-102">ICLRDataTarget3::Método GetExceptionContextRecord</span><span class="sxs-lookup"><span data-stu-id="95010-102">ICLRDataTarget3::GetExceptionContextRecord Method</span></span>
<span data-ttu-id="95010-103">Chamado pelo serviço de acesso a dados do CLR (Common Language Runtime) para recuperar o registro de contexto associado ao processo de destino.</span><span class="sxs-lookup"><span data-stu-id="95010-103">Called by the common language runtime (CLR) data access services to retrieve the context record associated with the target process.</span></span> <span data-ttu-id="95010-104">Por exemplo, para um destino de despejo de memória, isso seria equivalente para o registro de contexto passado por meio de `ExceptionParam` argumento para o [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360\(v=vs.85\).aspx) função na biblioteca do Windows depurar ajuda (DbgHelp).</span><span class="sxs-lookup"><span data-stu-id="95010-104">For example, for a dump target, this would be equivalent to the context record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360\(v=vs.85\).aspx) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95010-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="95010-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="95010-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="95010-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="95010-107">[in] O tamanho do buffer de entrada, em bytes.</span><span class="sxs-lookup"><span data-stu-id="95010-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="95010-108">Deve ser grande o suficiente para acomodar o registro de contexto.</span><span class="sxs-lookup"><span data-stu-id="95010-108">This must be large enough to accommodate the context record.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="95010-109">[out] Um ponteiro para um tipo `ULONG32` que recebe o número de bytes realmente gravados no buffer.</span><span class="sxs-lookup"><span data-stu-id="95010-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="95010-110">[out] Um ponteiro para um buffer de memória que recebe uma cópia do registro de contexto.</span><span class="sxs-lookup"><span data-stu-id="95010-110">[out] A pointer to a memory buffer that receives a copy of the context record.</span></span> <span data-ttu-id="95010-111">O registro de exceção é retornado como um [contexto](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx) tipo.</span><span class="sxs-lookup"><span data-stu-id="95010-111">The exception record is returned as a [CONTEXT](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="95010-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="95010-112">Return Value</span></span>  
 <span data-ttu-id="95010-113">O valor retornado é `S_OK` em caso de êxito, ou um código de falha `HRESULT` em caso de falha.</span><span class="sxs-lookup"><span data-stu-id="95010-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="95010-114">Os códigos `HRESULT` podem incluir, entre outros:</span><span class="sxs-lookup"><span data-stu-id="95010-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="95010-115">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="95010-115">Return code</span></span>|<span data-ttu-id="95010-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="95010-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="95010-117">O método foi bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="95010-117">Method succeeded.</span></span> <span data-ttu-id="95010-118">O registro de contexto foi copiado no buffer de saída.</span><span class="sxs-lookup"><span data-stu-id="95010-118">The context record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="95010-119">Nenhum registro de contexto está associado ao destino.</span><span class="sxs-lookup"><span data-stu-id="95010-119">No context record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="95010-120">O tamanho do buffer de entrada não é grande o suficiente para acomodar o registro de contexto.</span><span class="sxs-lookup"><span data-stu-id="95010-120">The input buffer size is not large enough to accommodate the context record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95010-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="95010-121">Remarks</span></span>  
 <span data-ttu-id="95010-122">[CONTEXTO](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx) é uma estrutura específica de plataforma definida em cabeçalhos fornecidos pelo SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="95010-122">[CONTEXT](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx) is a platform-specific structure defined in headers provided by the Windows SDK.</span></span>  
  
 <span data-ttu-id="95010-123">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="95010-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95010-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="95010-124">Requirements</span></span>  
 <span data-ttu-id="95010-125">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95010-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95010-126">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="95010-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="95010-127">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95010-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95010-128">**Versões do .NET framework:**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95010-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95010-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95010-129">See Also</span></span>  
 [<span data-ttu-id="95010-130">Interface ICLRDataTarget3</span><span class="sxs-lookup"><span data-stu-id="95010-130">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [<span data-ttu-id="95010-131">Método GetExceptionRecord</span><span class="sxs-lookup"><span data-stu-id="95010-131">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)  
 [<span data-ttu-id="95010-132">Método GetExceptionThreadID</span><span class="sxs-lookup"><span data-stu-id="95010-132">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
