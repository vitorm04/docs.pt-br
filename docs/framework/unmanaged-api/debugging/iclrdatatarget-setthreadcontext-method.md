---
title: Método ICLRDataTarget::SetThreadContext
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::SetThreadContext
helpviewer_keywords:
- SetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::SetThreadContext method [.NET Framework debugging]
ms.assetid: 103c8502-81fe-40d7-9c1e-9008d8fb19e1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9018ccc27d0afc35b9dfa2d2ebad323c9150ae60
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580688"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a><span data-ttu-id="c56cc-102">Método ICLRDataTarget::SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="c56cc-102">ICLRDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="c56cc-103">Define o contexto atual do thread especificado no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="c56cc-103">Sets the current context of the specified thread in the target process.</span></span> <span data-ttu-id="c56cc-104">Esse método é chamado pelo serviço de acesso de dados do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="c56cc-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c56cc-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c56cc-105">Syntax</span></span>  
  
```  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]   
         BYTE               *context  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c56cc-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c56cc-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="c56cc-107">[in] O identificador de sistema operacional de um thread no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="c56cc-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="c56cc-108">[in] O tamanho do contexto.</span><span class="sxs-lookup"><span data-stu-id="c56cc-108">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="c56cc-109">[in] Ponteiro para um buffer que contém o contexto.</span><span class="sxs-lookup"><span data-stu-id="c56cc-109">[in] Pointer to a buffer containing the context.</span></span>  
  
 <span data-ttu-id="c56cc-110">Os dados do `context` buffer será no formato de Win32 `CONTEXT` estrutura.</span><span class="sxs-lookup"><span data-stu-id="c56cc-110">The data in the `context` buffer will be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="c56cc-111">O contexto Especifica dados de registro específicas do processador, portanto, a definição do Win32 `CONTEXT` estrutura depende da arquitetura do processador.</span><span class="sxs-lookup"><span data-stu-id="c56cc-111">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="c56cc-112">Consulte o arquivo de cabeçalho de Winnt. H a definição de Win32 `CONTEXT` estrutura.</span><span class="sxs-lookup"><span data-stu-id="c56cc-112">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c56cc-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="c56cc-113">Remarks</span></span>  
 <span data-ttu-id="c56cc-114">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="c56cc-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c56cc-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c56cc-115">Requirements</span></span>  
 <span data-ttu-id="c56cc-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c56cc-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c56cc-117">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="c56cc-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="c56cc-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c56cc-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c56cc-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c56cc-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c56cc-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c56cc-120">See also</span></span>
- [<span data-ttu-id="c56cc-121">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="c56cc-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
