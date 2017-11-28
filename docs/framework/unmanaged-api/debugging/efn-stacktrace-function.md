---
title: "Função _EFN_StackTrace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _EFN_StackTrace
api_location: mscordbi.dll
api_type: COM
f1_keywords: _EFN_StackTrace
helpviewer_keywords: _EFN_StackTrace function [.NET Framework debugging]
ms.assetid: caea7754-867c-4360-a65c-5ced4408fd9d
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 031812b2c286c5647afb9c88882f22e2c7c3addf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="efnstacktrace-function"></a><span data-ttu-id="61ae5-102">Função _EFN_StackTrace</span><span class="sxs-lookup"><span data-stu-id="61ae5-102">_EFN_StackTrace Function</span></span>
<span data-ttu-id="61ae5-103">Fornece uma representação de texto de um rastreamento de pilha gerenciada e uma matriz de `CONTEXT` registra, uma para cada transição entre não gerenciados e código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="61ae5-103">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61ae5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="61ae5-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="61ae5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="61ae5-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="61ae5-106">[in] O cliente que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="61ae5-106">[in] The client being debugged.</span></span>  
  
 `wszTextOut`  
 <span data-ttu-id="61ae5-107">[out] A representação de texto de rastreamento de pilha.</span><span class="sxs-lookup"><span data-stu-id="61ae5-107">[out] The text representation of the stack trace.</span></span>  
  
 `puiTextLength`  
 <span data-ttu-id="61ae5-108">[out] Um ponteiro para o número de caracteres em `wszTextOut`.</span><span class="sxs-lookup"><span data-stu-id="61ae5-108">[out] A pointer to the number of characters in `wszTextOut`.</span></span>  
  
 `pTransitionContexts`  
 <span data-ttu-id="61ae5-109">[out] A matriz de contextos de transição.</span><span class="sxs-lookup"><span data-stu-id="61ae5-109">[out] The array of transition contexts.</span></span>  
  
 `puiTransitionContextCount`  
 <span data-ttu-id="61ae5-110">[out] Um ponteiro para o número de contextos de transição na matriz.</span><span class="sxs-lookup"><span data-stu-id="61ae5-110">[out] A pointer to the number of transition contexts in the array.</span></span>  
  
 `uiSizeOfContext`  
 <span data-ttu-id="61ae5-111">[in] O tamanho da estrutura de contexto.</span><span class="sxs-lookup"><span data-stu-id="61ae5-111">[in] The size of the context structure.</span></span>  
  
 `Flags`  
 <span data-ttu-id="61ae5-112">[in] Defina como 0 ou SOS_STACKTRACE_SHOWADDRESSES (0x01) para mostrar o registro EBP e o ponteiro de pilha enter (ESP) na frente de cada `module!functionname` linha.</span><span class="sxs-lookup"><span data-stu-id="61ae5-112">[in] Set to either 0 or SOS_STACKTRACE_SHOWADDRESSES (0x01) to show the EBP register and the enter stack pointer (ESP) in front of each `module!functionname` line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61ae5-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="61ae5-113">Remarks</span></span>  
 <span data-ttu-id="61ae5-114">O `_EFN_StackTrace` estrutura pode ser chamada de uma interface programática WinDbg.</span><span class="sxs-lookup"><span data-stu-id="61ae5-114">The `_EFN_StackTrace` structure can be called from a WinDbg programmatic interface.</span></span> <span data-ttu-id="61ae5-115">Parâmetros são usados da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="61ae5-115">Parameters are used as follows:</span></span>  
  
-   <span data-ttu-id="61ae5-116">Se `wszTextOut` é nulo e `puiTextLength` é não nulo, a função retorna o comprimento da cadeia de caracteres em `puiTextLength`.</span><span class="sxs-lookup"><span data-stu-id="61ae5-116">If `wszTextOut` is null and `puiTextLength` is not null, the function returns the string length in `puiTextLength`.</span></span>  
  
-   <span data-ttu-id="61ae5-117">Se `wszTextOut` é não nulo, a função armazena o texto em `wszTextOut` até o local indicado pelo `puiTextLength`.</span><span class="sxs-lookup"><span data-stu-id="61ae5-117">If `wszTextOut` is not null, the function stores text in `wszTextOut` up to the location indicated by `puiTextLength`.</span></span> <span data-ttu-id="61ae5-118">Retorna com êxito se não havia espaço suficiente no buffer ou E_OUTOFMEMORY de retorna se o buffer não era longa o suficiente.</span><span class="sxs-lookup"><span data-stu-id="61ae5-118">It returns successfully if there was enough room in the buffer, or returns E_OUTOFMEMORY if the buffer was not long enough.</span></span>  
  
-   <span data-ttu-id="61ae5-119">A parte de transição da função será ignorada se `pTransitionContexts` e `puiTransitionContextCount` são nulos.</span><span class="sxs-lookup"><span data-stu-id="61ae5-119">The transition portion of the function is ignored if `pTransitionContexts` and `puiTransitionContextCount` are both null.</span></span> <span data-ttu-id="61ae5-120">Nesse caso, a função fornece chamadores com saída de texto de apenas os nomes de função.</span><span class="sxs-lookup"><span data-stu-id="61ae5-120">In this case, the function provides callers with text output of only the function names.</span></span>  
  
-   <span data-ttu-id="61ae5-121">Se `pTransitionContexts` é nulo e `puiTransitionContextCount` é não nulo, a função retorna o número necessário de entradas de contexto em `puiTransitionContextCount`.</span><span class="sxs-lookup"><span data-stu-id="61ae5-121">If `pTransitionContexts` is null and `puiTransitionContextCount` is not null, the function returns the necessary number of context entries in `puiTransitionContextCount`.</span></span>  
  
-   <span data-ttu-id="61ae5-122">Se `pTransitionContexts` é não nulo, a função tratará como uma matriz de estruturas de comprimento `puiTransitionContextCount`.</span><span class="sxs-lookup"><span data-stu-id="61ae5-122">If `pTransitionContexts` is not null, the function treats it as an array of structures of length `puiTransitionContextCount`.</span></span> <span data-ttu-id="61ae5-123">O tamanho da estrutura é determinado pelo `uiSizeOfContext`, e deve ser o tamanho do [SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) ou `CONTEXT` para a arquitetura.</span><span class="sxs-lookup"><span data-stu-id="61ae5-123">The structure size is given by `uiSizeOfContext`, and must be the size of [SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) or `CONTEXT` for the architecture.</span></span>  
  
-   <span data-ttu-id="61ae5-124">`wszTextOut`é escrito no seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="61ae5-124">`wszTextOut` is written in the following format:</span></span>  
  
    ```  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
-   <span data-ttu-id="61ae5-125">Se o deslocamento em hexadecimal é 0x0, deslocamento não será gravado.</span><span class="sxs-lookup"><span data-stu-id="61ae5-125">If the offset in hex is 0x0, no offset is written.</span></span>  
  
-   <span data-ttu-id="61ae5-126">Não se houver nenhum código gerenciado no thread no momento no contexto, a função retornará SOS_E_NOMANAGEDCODE.</span><span class="sxs-lookup"><span data-stu-id="61ae5-126">If there is no managed code on the thread currently in context, the function returns SOS_E_NOMANAGEDCODE.</span></span>  
  
-   <span data-ttu-id="61ae5-127">O `Flags` parâmetro é 0 ou SOS_STACKTRACE_SHOWADDRESSES para ver EBP e ESP na frente de cada `module!functionname` linha.</span><span class="sxs-lookup"><span data-stu-id="61ae5-127">The `Flags` parameter is either 0 or SOS_STACKTRACE_SHOWADDRESSES to see EBP and ESP in front of each `module!functionname` line.</span></span> <span data-ttu-id="61ae5-128">Por padrão, é 0.</span><span class="sxs-lookup"><span data-stu-id="61ae5-128">By default, it is 0.</span></span>  
  
    ```  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a><span data-ttu-id="61ae5-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="61ae5-129">Requirements</span></span>  
 <span data-ttu-id="61ae5-130">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61ae5-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61ae5-131">**Cabeçalho:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="61ae5-131">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="61ae5-132">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61ae5-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61ae5-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61ae5-133">See Also</span></span>  
 [<span data-ttu-id="61ae5-134">Depurando funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="61ae5-134">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
