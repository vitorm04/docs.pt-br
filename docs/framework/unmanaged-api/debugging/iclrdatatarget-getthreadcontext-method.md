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
ms.openlocfilehash: a4ce7b90b417e0126337283ff16790f136cb16fc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407682"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a><span data-ttu-id="5eb2c-102">Método ICLRDataTarget::GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="5eb2c-102">ICLRDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="5eb2c-103">Obtém o contexto de execução atual de determinado thread no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="5eb2c-103">Gets the current execution context for the given thread in the target process.</span></span> <span data-ttu-id="5eb2c-104">Este método é chamado pelos serviços de acesso de dados de tempo de execução linguagem comuns.</span><span class="sxs-lookup"><span data-stu-id="5eb2c-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5eb2c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5eb2c-105">Syntax</span></span>  
  
```  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]   
        BYTE                *context  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5eb2c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5eb2c-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="5eb2c-107">[in] O identificador de sistema operacional de um thread no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="5eb2c-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="5eb2c-108">[in] Sinalizadores que especificam quais partes do contexto para retornar.</span><span class="sxs-lookup"><span data-stu-id="5eb2c-108">[in] Flags that specify which parts of the context to return.</span></span> <span data-ttu-id="5eb2c-109">A implementação irá retornar pelo menos essas partes do contexto.</span><span class="sxs-lookup"><span data-stu-id="5eb2c-109">The implementation will return at least these parts of the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="5eb2c-110">[in] O tamanho do contexto.</span><span class="sxs-lookup"><span data-stu-id="5eb2c-110">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="5eb2c-111">[out] Ponteiro para um buffer no qual colocar o contexto.</span><span class="sxs-lookup"><span data-stu-id="5eb2c-111">[out] Pointer to a buffer in which to place the context.</span></span>  
  
 <span data-ttu-id="5eb2c-112">Os dados de `context` buffer deve estar no formato de Win32 `CONTEXT` estrutura.</span><span class="sxs-lookup"><span data-stu-id="5eb2c-112">The data in the `context` buffer must be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="5eb2c-113">O contexto Especifica dados de registro específicos de processador, portanto a definição de Win32 `CONTEXT` estrutura depende da arquitetura do processador.</span><span class="sxs-lookup"><span data-stu-id="5eb2c-113">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="5eb2c-114">Consulte o arquivo de cabeçalho Winnt. H para a definição do Win32 `CONTEXT` estrutura.</span><span class="sxs-lookup"><span data-stu-id="5eb2c-114">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5eb2c-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="5eb2c-115">Remarks</span></span>  
 <span data-ttu-id="5eb2c-116">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="5eb2c-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5eb2c-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5eb2c-117">Requirements</span></span>  
 <span data-ttu-id="5eb2c-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5eb2c-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5eb2c-119">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="5eb2c-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="5eb2c-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5eb2c-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5eb2c-121">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5eb2c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5eb2c-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5eb2c-122">See Also</span></span>  
 [<span data-ttu-id="5eb2c-123">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="5eb2c-123">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
