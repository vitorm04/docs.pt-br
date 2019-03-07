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
ms.openlocfilehash: 7c2e1dc374a5205c774e4470363b38c604fa0862
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500493"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a><span data-ttu-id="7ccd9-102">Método ICLRDataTarget::GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="7ccd9-102">ICLRDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="7ccd9-103">Obtém o contexto de execução atual para o determinado thread no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="7ccd9-103">Gets the current execution context for the given thread in the target process.</span></span> <span data-ttu-id="7ccd9-104">Esse método é chamado pelo serviço de acesso de dados do common language runtime.</span><span class="sxs-lookup"><span data-stu-id="7ccd9-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ccd9-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7ccd9-105">Syntax</span></span>  
  
```  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]   
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ccd9-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7ccd9-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="7ccd9-107">[in] O identificador de sistema operacional de um thread no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="7ccd9-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="7ccd9-108">[in] Sinalizadores que especificam quais partes do contexto para retornar.</span><span class="sxs-lookup"><span data-stu-id="7ccd9-108">[in] Flags that specify which parts of the context to return.</span></span> <span data-ttu-id="7ccd9-109">A implementação retornará ao menos estas partes do contexto.</span><span class="sxs-lookup"><span data-stu-id="7ccd9-109">The implementation will return at least these parts of the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="7ccd9-110">[in] O tamanho do contexto.</span><span class="sxs-lookup"><span data-stu-id="7ccd9-110">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="7ccd9-111">[out] Ponteiro para um buffer no qual colocar o contexto.</span><span class="sxs-lookup"><span data-stu-id="7ccd9-111">[out] Pointer to a buffer in which to place the context.</span></span>  
  
 <span data-ttu-id="7ccd9-112">Os dados do `context` buffer deve estar no formato do Win32 `CONTEXT` estrutura.</span><span class="sxs-lookup"><span data-stu-id="7ccd9-112">The data in the `context` buffer must be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="7ccd9-113">O contexto Especifica dados de registro específicas do processador, portanto, a definição do Win32 `CONTEXT` estrutura depende da arquitetura do processador.</span><span class="sxs-lookup"><span data-stu-id="7ccd9-113">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="7ccd9-114">Consulte o arquivo de cabeçalho de Winnt. H a definição de Win32 `CONTEXT` estrutura.</span><span class="sxs-lookup"><span data-stu-id="7ccd9-114">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ccd9-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="7ccd9-115">Remarks</span></span>  
 <span data-ttu-id="7ccd9-116">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="7ccd9-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ccd9-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7ccd9-117">Requirements</span></span>  
 <span data-ttu-id="7ccd9-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ccd9-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ccd9-119">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="7ccd9-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="7ccd9-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ccd9-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ccd9-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ccd9-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ccd9-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7ccd9-122">See also</span></span>
- [<span data-ttu-id="7ccd9-123">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="7ccd9-123">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
