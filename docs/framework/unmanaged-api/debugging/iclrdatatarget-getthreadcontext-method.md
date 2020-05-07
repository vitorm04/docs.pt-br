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
ms.openlocfilehash: 5c0fb023dd355f3a9c1ed846913f86b354592ed5
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860610"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a><span data-ttu-id="0b258-102">Método ICLRDataTarget::GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="0b258-102">ICLRDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="0b258-103">Obtém o contexto de execução atual para o thread determinado no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="0b258-103">Gets the current execution context for the given thread in the target process.</span></span> <span data-ttu-id="0b258-104">Esse método é chamado pelo Common Language Runtime Data Access Services.</span><span class="sxs-lookup"><span data-stu-id="0b258-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b258-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0b258-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b258-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0b258-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="0b258-107">no O identificador do sistema operacional de um thread no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="0b258-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="0b258-108">no Sinalizadores que especificam quais partes do contexto retornar.</span><span class="sxs-lookup"><span data-stu-id="0b258-108">[in] Flags that specify which parts of the context to return.</span></span> <span data-ttu-id="0b258-109">A implementação retornará pelo menos essas partes do contexto.</span><span class="sxs-lookup"><span data-stu-id="0b258-109">The implementation will return at least these parts of the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="0b258-110">no O tamanho do contexto.</span><span class="sxs-lookup"><span data-stu-id="0b258-110">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="0b258-111">fora Ponteiro para um buffer no qual o contexto será colocado.</span><span class="sxs-lookup"><span data-stu-id="0b258-111">[out] Pointer to a buffer in which to place the context.</span></span>  
  
 <span data-ttu-id="0b258-112">Os dados no `context` buffer devem estar no formato da estrutura do Win32 `CONTEXT` .</span><span class="sxs-lookup"><span data-stu-id="0b258-112">The data in the `context` buffer must be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="0b258-113">O contexto especifica dados de registro específicos do processador, de modo que a definição `CONTEXT` da estrutura do Win32 depende da arquitetura do processador.</span><span class="sxs-lookup"><span data-stu-id="0b258-113">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="0b258-114">Consulte o arquivo de cabeçalho WinNT. h para obter a definição da estrutura `CONTEXT` do Win32.</span><span class="sxs-lookup"><span data-stu-id="0b258-114">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b258-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="0b258-115">Remarks</span></span>  
 <span data-ttu-id="0b258-116">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="0b258-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b258-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0b258-117">Requirements</span></span>  
 <span data-ttu-id="0b258-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b258-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b258-119">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="0b258-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="0b258-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b258-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b258-121">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b258-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b258-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="0b258-122">See also</span></span>

- [<span data-ttu-id="0b258-123">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="0b258-123">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
