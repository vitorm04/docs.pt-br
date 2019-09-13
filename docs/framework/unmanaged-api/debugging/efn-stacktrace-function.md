---
title: Função _EFN_StackTrace
ms.date: 03/30/2017
api_name:
- _EFN_StackTrace
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_StackTrace
helpviewer_keywords:
- _EFN_StackTrace function [.NET Framework debugging]
ms.assetid: caea7754-867c-4360-a65c-5ced4408fd9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9035d9a53c4b0c8822b79e641aef092b4a48c418
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895040"
---
# <a name="_efn_stacktrace-function"></a><span data-ttu-id="57169-102">\_Função\_EFN StackTrace</span><span class="sxs-lookup"><span data-stu-id="57169-102">\_EFN\_StackTrace Function</span></span>
<span data-ttu-id="57169-103">Fornece uma representação de texto de um rastreamento de pilha gerenciado e uma `CONTEXT` matriz de registros, um para cada transição entre código gerenciado e não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="57169-103">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57169-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="57169-104">Syntax</span></span>  
  
```cpp  
HRESULT CALLBACK _EFN_StackTrace(  
    [in]  PDEBUG_CLIENT  Client,  
    [out] WCHAR          wszTextOut[],  
    [out] size_t         *puiTextLength,  
    [out] LPVOID         pTransitionContexts,  
    [out] size_t         *puiTransitionContextCount,  
    [in]  size_t         uiSizeOfContext,  
    [in]  DWORD          Flags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57169-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="57169-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="57169-106">no O cliente que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="57169-106">[in] The client being debugged.</span></span>  
  
 `wszTextOut`  
 <span data-ttu-id="57169-107">fora A representação de texto do rastreamento de pilha.</span><span class="sxs-lookup"><span data-stu-id="57169-107">[out] The text representation of the stack trace.</span></span>  
  
 `puiTextLength`  
 <span data-ttu-id="57169-108">fora Um ponteiro para o número de caracteres em `wszTextOut`.</span><span class="sxs-lookup"><span data-stu-id="57169-108">[out] A pointer to the number of characters in `wszTextOut`.</span></span>  
  
 `pTransitionContexts`  
 <span data-ttu-id="57169-109">fora A matriz de contextos de transição.</span><span class="sxs-lookup"><span data-stu-id="57169-109">[out] The array of transition contexts.</span></span>  
  
 `puiTransitionContextCount`  
 <span data-ttu-id="57169-110">fora Um ponteiro para o número de contextos de transição na matriz.</span><span class="sxs-lookup"><span data-stu-id="57169-110">[out] A pointer to the number of transition contexts in the array.</span></span>  
  
 `uiSizeOfContext`  
 <span data-ttu-id="57169-111">no O tamanho da estrutura de contexto.</span><span class="sxs-lookup"><span data-stu-id="57169-111">[in] The size of the context structure.</span></span>  
  
 `Flags`  
 <span data-ttu-id="57169-112">no Defina como 0 ou SOS_STACKTRACE_SHOWADDRESSES (0x01) para mostrar o registro de EBP e o ponteiro de pilha Enter (ESP) na frente de `module!functionname` cada linha.</span><span class="sxs-lookup"><span data-stu-id="57169-112">[in] Set to either 0 or SOS_STACKTRACE_SHOWADDRESSES (0x01) to show the EBP register and the enter stack pointer (ESP) in front of each `module!functionname` line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57169-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="57169-113">Remarks</span></span>  
 <span data-ttu-id="57169-114">A `_EFN_StackTrace` estrutura pode ser chamada de uma interface programática do WinDbg.</span><span class="sxs-lookup"><span data-stu-id="57169-114">The `_EFN_StackTrace` structure can be called from a WinDbg programmatic interface.</span></span> <span data-ttu-id="57169-115">Os parâmetros são usados da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="57169-115">Parameters are used as follows:</span></span>  
  
- <span data-ttu-id="57169-116">Se `wszTextOut` for NULL e `puiTextLength` não for NULL, a função retornará o comprimento da cadeia `puiTextLength`de caracteres em.</span><span class="sxs-lookup"><span data-stu-id="57169-116">If `wszTextOut` is null and `puiTextLength` is not null, the function returns the string length in `puiTextLength`.</span></span>  
  
- <span data-ttu-id="57169-117">Se `wszTextOut` não for NULL, a função armazenará texto `wszTextOut` em até o local indicado por `puiTextLength`.</span><span class="sxs-lookup"><span data-stu-id="57169-117">If `wszTextOut` is not null, the function stores text in `wszTextOut` up to the location indicated by `puiTextLength`.</span></span> <span data-ttu-id="57169-118">Ele retorna com êxito se havia espaço suficiente no buffer ou retorna E_OUTOFMEMORY se o buffer não era longo o suficiente.</span><span class="sxs-lookup"><span data-stu-id="57169-118">It returns successfully if there was enough room in the buffer, or returns E_OUTOFMEMORY if the buffer was not long enough.</span></span>  
  
- <span data-ttu-id="57169-119">A parte de transição da função será ignorada `pTransitionContexts` se `puiTransitionContextCount` e for nula.</span><span class="sxs-lookup"><span data-stu-id="57169-119">The transition portion of the function is ignored if `pTransitionContexts` and `puiTransitionContextCount` are both null.</span></span> <span data-ttu-id="57169-120">Nesse caso, a função fornece chamadores com a saída de texto apenas dos nomes de função.</span><span class="sxs-lookup"><span data-stu-id="57169-120">In this case, the function provides callers with text output of only the function names.</span></span>  
  
- <span data-ttu-id="57169-121">Se `pTransitionContexts` for NULL e `puiTransitionContextCount` não for NULL, a função retornará o número necessário de entradas de contexto `puiTransitionContextCount`no.</span><span class="sxs-lookup"><span data-stu-id="57169-121">If `pTransitionContexts` is null and `puiTransitionContextCount` is not null, the function returns the necessary number of context entries in `puiTransitionContextCount`.</span></span>  
  
- <span data-ttu-id="57169-122">Se `pTransitionContexts` não for NULL, a função a tratará como uma matriz de estruturas de `puiTransitionContextCount`comprimento.</span><span class="sxs-lookup"><span data-stu-id="57169-122">If `pTransitionContexts` is not null, the function treats it as an array of structures of length `puiTransitionContextCount`.</span></span> <span data-ttu-id="57169-123">O tamanho da estrutura é fornecido `uiSizeOfContext`por e deve ser o tamanho de [SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) ou `CONTEXT` para a arquitetura.</span><span class="sxs-lookup"><span data-stu-id="57169-123">The structure size is given by `uiSizeOfContext`, and must be the size of [SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) or `CONTEXT` for the architecture.</span></span>  
  
- <span data-ttu-id="57169-124">`wszTextOut`é escrito no seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="57169-124">`wszTextOut` is written in the following format:</span></span>  
  
    ```output  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
- <span data-ttu-id="57169-125">Se o deslocamento em Hex for 0x0, nenhum deslocamento será gravado.</span><span class="sxs-lookup"><span data-stu-id="57169-125">If the offset in hex is 0x0, no offset is written.</span></span>  
  
- <span data-ttu-id="57169-126">Se não houver nenhum código gerenciado no thread atualmente no contexto, a função retornará SOS_E_NOMANAGEDCODE.</span><span class="sxs-lookup"><span data-stu-id="57169-126">If there is no managed code on the thread currently in context, the function returns SOS_E_NOMANAGEDCODE.</span></span>  
  
- <span data-ttu-id="57169-127">O `Flags` parâmetro é 0 ou SOS_STACKTRACE_SHOWADDRESSES para ver EBP e ESP na frente de cada `module!functionname` linha.</span><span class="sxs-lookup"><span data-stu-id="57169-127">The `Flags` parameter is either 0 or SOS_STACKTRACE_SHOWADDRESSES to see EBP and ESP in front of each `module!functionname` line.</span></span> <span data-ttu-id="57169-128">Por padrão, é 0.</span><span class="sxs-lookup"><span data-stu-id="57169-128">By default, it is 0.</span></span>  
  
    ```cpp  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a><span data-ttu-id="57169-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="57169-129">Requirements</span></span>  
 <span data-ttu-id="57169-130">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57169-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57169-131">**Cabeçalho:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="57169-131">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="57169-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57169-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57169-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="57169-133">See also</span></span>

- [<span data-ttu-id="57169-134">Depurando funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="57169-134">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
