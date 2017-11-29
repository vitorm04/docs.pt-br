---
title: "Método ICLRDataTarget::SetThreadContext"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.SetThreadContext
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::SetThreadContext
helpviewer_keywords:
- SetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::SetThreadContext method [.NET Framework debugging]
ms.assetid: 103c8502-81fe-40d7-9c1e-9008d8fb19e1
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e51cbafda76933d58bd60be8db7dd163a2dd59d3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdatatargetsetthreadcontext-method"></a><span data-ttu-id="4adec-102">Método ICLRDataTarget::SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="4adec-102">ICLRDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="4adec-103">Define o contexto atual do thread especificado no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="4adec-103">Sets the current context of the specified thread in the target process.</span></span> <span data-ttu-id="4adec-104">Este método é chamado, os serviços de acesso dados common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="4adec-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4adec-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4adec-105">Syntax</span></span>  
  
```  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]   
         BYTE               *context  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4adec-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4adec-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="4adec-107">[in] O identificador de sistema operacional de um thread no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="4adec-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="4adec-108">[in] O tamanho do contexto.</span><span class="sxs-lookup"><span data-stu-id="4adec-108">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="4adec-109">[in] Ponteiro para um buffer que contém o contexto.</span><span class="sxs-lookup"><span data-stu-id="4adec-109">[in] Pointer to a buffer containing the context.</span></span>  
  
 <span data-ttu-id="4adec-110">Os dados de `context` buffer será no formato do Win32 `CONTEXT` estrutura.</span><span class="sxs-lookup"><span data-stu-id="4adec-110">The data in the `context` buffer will be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="4adec-111">O contexto Especifica dados de registro específicos de processador, portanto a definição de Win32 `CONTEXT` estrutura depende da arquitetura do processador.</span><span class="sxs-lookup"><span data-stu-id="4adec-111">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="4adec-112">Consulte o arquivo de cabeçalho Winnt. H para a definição do Win32 `CONTEXT` estrutura.</span><span class="sxs-lookup"><span data-stu-id="4adec-112">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4adec-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="4adec-113">Remarks</span></span>  
 <span data-ttu-id="4adec-114">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="4adec-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4adec-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4adec-115">Requirements</span></span>  
 <span data-ttu-id="4adec-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4adec-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4adec-117">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="4adec-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="4adec-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4adec-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4adec-119">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4adec-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4adec-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4adec-120">See Also</span></span>  
 [<span data-ttu-id="4adec-121">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="4adec-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
