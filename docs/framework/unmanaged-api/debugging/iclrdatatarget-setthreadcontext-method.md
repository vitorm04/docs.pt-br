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
ms.openlocfilehash: d76a907434b12b85aaedeef169390ec6f0df724a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179123"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a><span data-ttu-id="71f0d-102">Método ICLRDataTarget::SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="71f0d-102">ICLRDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="71f0d-103">Define o contexto atual do segmento especificado no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="71f0d-103">Sets the current context of the specified thread in the target process.</span></span> <span data-ttu-id="71f0d-104">Esse método é chamado pelos serviços de acesso a dados do tempo de execução de idioma comum (CLR).</span><span class="sxs-lookup"><span data-stu-id="71f0d-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71f0d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="71f0d-105">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]
         BYTE               *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71f0d-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="71f0d-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="71f0d-107">[em] O identificador do sistema operacional de um segmento no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="71f0d-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="71f0d-108">[em] O tamanho do contexto.</span><span class="sxs-lookup"><span data-stu-id="71f0d-108">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="71f0d-109">[em] Ponteiro para um buffer contendo o contexto.</span><span class="sxs-lookup"><span data-stu-id="71f0d-109">[in] Pointer to a buffer containing the context.</span></span>  
  
 <span data-ttu-id="71f0d-110">Os dados `context` no buffer estarão no formato `CONTEXT` da estrutura Win32.</span><span class="sxs-lookup"><span data-stu-id="71f0d-110">The data in the `context` buffer will be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="71f0d-111">O contexto especifica dados de registro específicos do processador, `CONTEXT` de modo que a definição da estrutura Win32 depende da arquitetura do processador.</span><span class="sxs-lookup"><span data-stu-id="71f0d-111">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="71f0d-112">Consulte o arquivo de cabeçalho WinNT.h `CONTEXT` para a definição da estrutura Win32.</span><span class="sxs-lookup"><span data-stu-id="71f0d-112">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71f0d-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="71f0d-113">Remarks</span></span>  
 <span data-ttu-id="71f0d-114">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="71f0d-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71f0d-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="71f0d-115">Requirements</span></span>  
 <span data-ttu-id="71f0d-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71f0d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71f0d-117">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="71f0d-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="71f0d-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71f0d-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71f0d-119">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71f0d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71f0d-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="71f0d-120">See also</span></span>

- [<span data-ttu-id="71f0d-121">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="71f0d-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
