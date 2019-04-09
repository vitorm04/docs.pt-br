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
ms.openlocfilehash: dfbdbb389f9945ffeea649bcddd45bee8caf2496
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119984"
---
# <a name="efnstacktrace-function"></a><span data-ttu-id="b59e4-102">Função _EFN_StackTrace</span><span class="sxs-lookup"><span data-stu-id="b59e4-102">_EFN_StackTrace Function</span></span>
<span data-ttu-id="b59e4-103">Fornece uma representação de texto de um rastreamento de pilha gerenciada e uma matriz de `CONTEXT` registra, um para cada transição entre não gerenciado e código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b59e4-103">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b59e4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b59e4-104">Syntax</span></span>  
  
```  
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
  
## <a name="parameters"></a><span data-ttu-id="b59e4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b59e4-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="b59e4-106">[in] O cliente que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="b59e4-106">[in] The client being debugged.</span></span>  
  
 `wszTextOut`  
 <span data-ttu-id="b59e4-107">[out] A representação de texto de rastreamento de pilha.</span><span class="sxs-lookup"><span data-stu-id="b59e4-107">[out] The text representation of the stack trace.</span></span>  
  
 `puiTextLength`  
 <span data-ttu-id="b59e4-108">[out] Um ponteiro para o número de caracteres em `wszTextOut`.</span><span class="sxs-lookup"><span data-stu-id="b59e4-108">[out] A pointer to the number of characters in `wszTextOut`.</span></span>  
  
 `pTransitionContexts`  
 <span data-ttu-id="b59e4-109">[out] A matriz de contextos de transição.</span><span class="sxs-lookup"><span data-stu-id="b59e4-109">[out] The array of transition contexts.</span></span>  
  
 `puiTransitionContextCount`  
 <span data-ttu-id="b59e4-110">[out] Um ponteiro para o número de contextos de transição na matriz.</span><span class="sxs-lookup"><span data-stu-id="b59e4-110">[out] A pointer to the number of transition contexts in the array.</span></span>  
  
 `uiSizeOfContext`  
 <span data-ttu-id="b59e4-111">[in] O tamanho da estrutura de contexto.</span><span class="sxs-lookup"><span data-stu-id="b59e4-111">[in] The size of the context structure.</span></span>  
  
 `Flags`  
 <span data-ttu-id="b59e4-112">[in] Defina como 0 ou SOS_STACKTRACE_SHOWADDRESSES (0x01) para mostrar o registro EBP e o ponteiro de pilha de enter (ESP) na frente de cada `module!functionname` linha.</span><span class="sxs-lookup"><span data-stu-id="b59e4-112">[in] Set to either 0 or SOS_STACKTRACE_SHOWADDRESSES (0x01) to show the EBP register and the enter stack pointer (ESP) in front of each `module!functionname` line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b59e4-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="b59e4-113">Remarks</span></span>  
 <span data-ttu-id="b59e4-114">O `_EFN_StackTrace` estrutura pode ser chamada de uma interface programática do WinDbg.</span><span class="sxs-lookup"><span data-stu-id="b59e4-114">The `_EFN_StackTrace` structure can be called from a WinDbg programmatic interface.</span></span> <span data-ttu-id="b59e4-115">Parâmetros são usados da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b59e4-115">Parameters are used as follows:</span></span>  
  
-   <span data-ttu-id="b59e4-116">Se `wszTextOut` for null e `puiTextLength` for não nulo, a função retorna o comprimento da cadeia de caracteres em `puiTextLength`.</span><span class="sxs-lookup"><span data-stu-id="b59e4-116">If `wszTextOut` is null and `puiTextLength` is not null, the function returns the string length in `puiTextLength`.</span></span>  
  
-   <span data-ttu-id="b59e4-117">Se `wszTextOut` é diferente de null, a função armazena o texto no `wszTextOut` até o local indicado pelo `puiTextLength`.</span><span class="sxs-lookup"><span data-stu-id="b59e4-117">If `wszTextOut` is not null, the function stores text in `wszTextOut` up to the location indicated by `puiTextLength`.</span></span> <span data-ttu-id="b59e4-118">Retorna com êxito se não havia espaço suficiente no buffer ou retorna E_OUTOFMEMORY se o buffer não era longo o suficiente.</span><span class="sxs-lookup"><span data-stu-id="b59e4-118">It returns successfully if there was enough room in the buffer, or returns E_OUTOFMEMORY if the buffer was not long enough.</span></span>  
  
-   <span data-ttu-id="b59e4-119">A parte da transição da função será ignorada se `pTransitionContexts` e `puiTransitionContextCount` forem ambos nulos.</span><span class="sxs-lookup"><span data-stu-id="b59e4-119">The transition portion of the function is ignored if `pTransitionContexts` and `puiTransitionContextCount` are both null.</span></span> <span data-ttu-id="b59e4-120">Nesse caso, a função fornece chamadores com saída de texto de somente os nomes de função.</span><span class="sxs-lookup"><span data-stu-id="b59e4-120">In this case, the function provides callers with text output of only the function names.</span></span>  
  
-   <span data-ttu-id="b59e4-121">Se `pTransitionContexts` for null e `puiTransitionContextCount` for não nulo, a função retorna o número necessário de entradas de contexto no `puiTransitionContextCount`.</span><span class="sxs-lookup"><span data-stu-id="b59e4-121">If `pTransitionContexts` is null and `puiTransitionContextCount` is not null, the function returns the necessary number of context entries in `puiTransitionContextCount`.</span></span>  
  
-   <span data-ttu-id="b59e4-122">Se `pTransitionContexts` é diferente de null, a função tratará como uma matriz de estruturas de comprimento `puiTransitionContextCount`.</span><span class="sxs-lookup"><span data-stu-id="b59e4-122">If `pTransitionContexts` is not null, the function treats it as an array of structures of length `puiTransitionContextCount`.</span></span> <span data-ttu-id="b59e4-123">O tamanho da estrutura será determinado pelos `uiSizeOfContext`, e deve ser o tamanho de [SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) ou `CONTEXT` para a arquitetura.</span><span class="sxs-lookup"><span data-stu-id="b59e4-123">The structure size is given by `uiSizeOfContext`, and must be the size of [SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) or `CONTEXT` for the architecture.</span></span>  
  
-   `wszTextOut` <span data-ttu-id="b59e4-124">é escrito no seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="b59e4-124">is written in the following format:</span></span>  
  
    ```  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
-   <span data-ttu-id="b59e4-125">Se o deslocamento em hexadecimal é 0x0, deslocamento não será gravado.</span><span class="sxs-lookup"><span data-stu-id="b59e4-125">If the offset in hex is 0x0, no offset is written.</span></span>  
  
-   <span data-ttu-id="b59e4-126">Não se houver nenhum código gerenciado no thread atualmente no contexto, a função retorna SOS_E_NOMANAGEDCODE.</span><span class="sxs-lookup"><span data-stu-id="b59e4-126">If there is no managed code on the thread currently in context, the function returns SOS_E_NOMANAGEDCODE.</span></span>  
  
-   <span data-ttu-id="b59e4-127">O `Flags` parâmetro é 0 ou SOS_STACKTRACE_SHOWADDRESSES ver EBP e ESP na frente de cada `module!functionname` linha.</span><span class="sxs-lookup"><span data-stu-id="b59e4-127">The `Flags` parameter is either 0 or SOS_STACKTRACE_SHOWADDRESSES to see EBP and ESP in front of each `module!functionname` line.</span></span> <span data-ttu-id="b59e4-128">Por padrão, é 0.</span><span class="sxs-lookup"><span data-stu-id="b59e4-128">By default, it is 0.</span></span>  
  
    ```  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a><span data-ttu-id="b59e4-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b59e4-129">Requirements</span></span>  
 <span data-ttu-id="b59e4-130">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b59e4-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b59e4-131">**Cabeçalho:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="b59e4-131">**Header:** SOS_Stacktrace.h</span></span>  
  
 **<span data-ttu-id="b59e4-132">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="b59e4-132">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b59e4-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b59e4-133">See also</span></span>

- [<span data-ttu-id="b59e4-134">Depurando funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="b59e4-134">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
