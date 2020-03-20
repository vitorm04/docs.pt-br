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
ms.openlocfilehash: 3777ad4b12c7d0593c095c470aba81088137a859
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179177"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a><span data-ttu-id="39f55-102">Método ICLRDataTarget::GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="39f55-102">ICLRDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="39f55-103">Obtém o contexto de execução atual para o segmento dado no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="39f55-103">Gets the current execution context for the given thread in the target process.</span></span> <span data-ttu-id="39f55-104">Esse método é chamado pelos serviços comuns de acesso a dados em tempo de execução do idioma.</span><span class="sxs-lookup"><span data-stu-id="39f55-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39f55-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="39f55-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39f55-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="39f55-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="39f55-107">[em] O identificador do sistema operacional de um segmento no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="39f55-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="39f55-108">[em] Sinalizadores que especificam quais partes do contexto retornar.</span><span class="sxs-lookup"><span data-stu-id="39f55-108">[in] Flags that specify which parts of the context to return.</span></span> <span data-ttu-id="39f55-109">A implementação retornará pelo menos essas partes do contexto.</span><span class="sxs-lookup"><span data-stu-id="39f55-109">The implementation will return at least these parts of the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="39f55-110">[em] O tamanho do contexto.</span><span class="sxs-lookup"><span data-stu-id="39f55-110">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="39f55-111">[fora] Ponteiro para um buffer no qual colocar o contexto.</span><span class="sxs-lookup"><span data-stu-id="39f55-111">[out] Pointer to a buffer in which to place the context.</span></span>  
  
 <span data-ttu-id="39f55-112">Os dados `context` no buffer devem estar no formato `CONTEXT` da estrutura Win32.</span><span class="sxs-lookup"><span data-stu-id="39f55-112">The data in the `context` buffer must be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="39f55-113">O contexto especifica dados de registro específicos do processador, `CONTEXT` de modo que a definição da estrutura Win32 depende da arquitetura do processador.</span><span class="sxs-lookup"><span data-stu-id="39f55-113">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="39f55-114">Consulte o arquivo de cabeçalho WinNT.h `CONTEXT` para a definição da estrutura Win32.</span><span class="sxs-lookup"><span data-stu-id="39f55-114">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39f55-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="39f55-115">Remarks</span></span>  
 <span data-ttu-id="39f55-116">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="39f55-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39f55-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="39f55-117">Requirements</span></span>  
 <span data-ttu-id="39f55-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39f55-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39f55-119">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="39f55-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="39f55-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39f55-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39f55-121">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39f55-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39f55-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="39f55-122">See also</span></span>

- [<span data-ttu-id="39f55-123">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="39f55-123">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
