---
title: Método ICLRDataTarget::GetThreadContext
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetThreadContext
helpviewer_keywords:
- ICLRDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: b9d8c3b5-3a2e-4225-95d4-dd052c4532c3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88d563918709a6cf31d9c14a52bbd461ae004420
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116149"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a><span data-ttu-id="e678b-102">Método ICLRDataTarget::GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="e678b-102">ICLRDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="e678b-103">Obtém o contexto de execução atual para o determinado thread no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="e678b-103">Gets the current execution context for the given thread in the target process.</span></span> <span data-ttu-id="e678b-104">Esse método é chamado pelo serviço de acesso de dados do common language runtime.</span><span class="sxs-lookup"><span data-stu-id="e678b-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e678b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e678b-105">Syntax</span></span>  
  
```  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]   
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e678b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e678b-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="e678b-107">[in] O identificador de sistema operacional de um thread no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="e678b-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="e678b-108">[in] Sinalizadores que especificam quais partes do contexto para retornar.</span><span class="sxs-lookup"><span data-stu-id="e678b-108">[in] Flags that specify which parts of the context to return.</span></span> <span data-ttu-id="e678b-109">A implementação retornará ao menos estas partes do contexto.</span><span class="sxs-lookup"><span data-stu-id="e678b-109">The implementation will return at least these parts of the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="e678b-110">[in] O tamanho do contexto.</span><span class="sxs-lookup"><span data-stu-id="e678b-110">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="e678b-111">[out] Ponteiro para um buffer no qual colocar o contexto.</span><span class="sxs-lookup"><span data-stu-id="e678b-111">[out] Pointer to a buffer in which to place the context.</span></span>  
  
 <span data-ttu-id="e678b-112">Os dados do `context` buffer deve estar no formato do Win32 `CONTEXT` estrutura.</span><span class="sxs-lookup"><span data-stu-id="e678b-112">The data in the `context` buffer must be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="e678b-113">O contexto Especifica dados de registro específicas do processador, portanto, a definição do Win32 `CONTEXT` estrutura depende da arquitetura do processador.</span><span class="sxs-lookup"><span data-stu-id="e678b-113">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="e678b-114">Consulte o arquivo de cabeçalho de Winnt. H a definição de Win32 `CONTEXT` estrutura.</span><span class="sxs-lookup"><span data-stu-id="e678b-114">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e678b-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="e678b-115">Remarks</span></span>  
 <span data-ttu-id="e678b-116">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="e678b-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e678b-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e678b-117">Requirements</span></span>  
 <span data-ttu-id="e678b-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e678b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e678b-119">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="e678b-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="e678b-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e678b-120">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e678b-121">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="e678b-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e678b-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e678b-122">See also</span></span>

- [<span data-ttu-id="e678b-123">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="e678b-123">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
