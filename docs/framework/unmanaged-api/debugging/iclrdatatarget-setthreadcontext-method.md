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
ms.openlocfilehash: b8c4b4e585bba4df39a743273221f38ce14a9b9d
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860523"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a><span data-ttu-id="871a6-102">Método ICLRDataTarget::SetThreadContext</span><span class="sxs-lookup"><span data-stu-id="871a6-102">ICLRDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="871a6-103">Define o contexto atual do thread especificado no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="871a6-103">Sets the current context of the specified thread in the target process.</span></span> <span data-ttu-id="871a6-104">Esse método é chamado pelos serviços de acesso a dados do Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="871a6-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="871a6-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="871a6-105">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]
         BYTE               *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="871a6-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="871a6-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="871a6-107">no O identificador do sistema operacional de um thread no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="871a6-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="871a6-108">no O tamanho do contexto.</span><span class="sxs-lookup"><span data-stu-id="871a6-108">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="871a6-109">no Ponteiro para um buffer que contém o contexto.</span><span class="sxs-lookup"><span data-stu-id="871a6-109">[in] Pointer to a buffer containing the context.</span></span>  
  
 <span data-ttu-id="871a6-110">Os dados no `context` buffer estarão no formato da estrutura do Win32 `CONTEXT` .</span><span class="sxs-lookup"><span data-stu-id="871a6-110">The data in the `context` buffer will be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="871a6-111">O contexto especifica dados de registro específicos do processador, de modo que a definição `CONTEXT` da estrutura do Win32 depende da arquitetura do processador.</span><span class="sxs-lookup"><span data-stu-id="871a6-111">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="871a6-112">Consulte o arquivo de cabeçalho WinNT. h para obter a definição da estrutura `CONTEXT` do Win32.</span><span class="sxs-lookup"><span data-stu-id="871a6-112">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="871a6-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="871a6-113">Remarks</span></span>  
 <span data-ttu-id="871a6-114">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="871a6-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="871a6-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="871a6-115">Requirements</span></span>  
 <span data-ttu-id="871a6-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="871a6-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="871a6-117">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="871a6-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="871a6-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="871a6-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="871a6-119">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="871a6-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="871a6-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="871a6-120">See also</span></span>

- [<span data-ttu-id="871a6-121">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="871a6-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
