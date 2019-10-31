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
ms.openlocfilehash: 272856c7eedbdc577158edcc463535a7946bb060
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122984"
---
# <a name="_efn_stacktrace-function"></a><span data-ttu-id="ba4fe-102">\_EFN\_a função StackTrace</span><span class="sxs-lookup"><span data-stu-id="ba4fe-102">\_EFN\_StackTrace Function</span></span>
<span data-ttu-id="ba4fe-103">Fornece uma representação de texto de um rastreamento de pilha gerenciado e uma matriz de registros de `CONTEXT`, um para cada transição entre código gerenciado e não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="ba4fe-103">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba4fe-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ba4fe-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ba4fe-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ba4fe-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="ba4fe-106">no O cliente que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="ba4fe-106">[in] The client being debugged.</span></span>  
  
 `wszTextOut`  
 <span data-ttu-id="ba4fe-107">fora A representação de texto do rastreamento de pilha.</span><span class="sxs-lookup"><span data-stu-id="ba4fe-107">[out] The text representation of the stack trace.</span></span>  
  
 `puiTextLength`  
 <span data-ttu-id="ba4fe-108">fora Um ponteiro para o número de caracteres em `wszTextOut`.</span><span class="sxs-lookup"><span data-stu-id="ba4fe-108">[out] A pointer to the number of characters in `wszTextOut`.</span></span>  
  
 `pTransitionContexts`  
 <span data-ttu-id="ba4fe-109">fora A matriz de contextos de transição.</span><span class="sxs-lookup"><span data-stu-id="ba4fe-109">[out] The array of transition contexts.</span></span>  
  
 `puiTransitionContextCount`  
 <span data-ttu-id="ba4fe-110">fora Um ponteiro para o número de contextos de transição na matriz.</span><span class="sxs-lookup"><span data-stu-id="ba4fe-110">[out] A pointer to the number of transition contexts in the array.</span></span>  
  
 `uiSizeOfContext`  
 <span data-ttu-id="ba4fe-111">no O tamanho da estrutura de contexto.</span><span class="sxs-lookup"><span data-stu-id="ba4fe-111">[in] The size of the context structure.</span></span>  
  
 `Flags`  
 <span data-ttu-id="ba4fe-112">no Defina como 0 ou SOS_STACKTRACE_SHOWADDRESSES (0x01) para mostrar o registro de EBP e o ponteiro de pilha Enter (ESP) na frente de cada linha de `module!functionname`.</span><span class="sxs-lookup"><span data-stu-id="ba4fe-112">[in] Set to either 0 or SOS_STACKTRACE_SHOWADDRESSES (0x01) to show the EBP register and the enter stack pointer (ESP) in front of each `module!functionname` line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba4fe-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="ba4fe-113">Remarks</span></span>  
 <span data-ttu-id="ba4fe-114">A estrutura de `_EFN_StackTrace` pode ser chamada de uma interface programática do WinDbg.</span><span class="sxs-lookup"><span data-stu-id="ba4fe-114">The `_EFN_StackTrace` structure can be called from a WinDbg programmatic interface.</span></span> <span data-ttu-id="ba4fe-115">Os parâmetros são usados da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="ba4fe-115">Parameters are used as follows:</span></span>  
  
- <span data-ttu-id="ba4fe-116">Se `wszTextOut` for NULL e `puiTextLength` não for NULL, a função retornará o comprimento da cadeia de caracteres em `puiTextLength`.</span><span class="sxs-lookup"><span data-stu-id="ba4fe-116">If `wszTextOut` is null and `puiTextLength` is not null, the function returns the string length in `puiTextLength`.</span></span>  
  
- <span data-ttu-id="ba4fe-117">Se `wszTextOut` não for NULL, a função armazenará texto em `wszTextOut` até o local indicado por `puiTextLength`.</span><span class="sxs-lookup"><span data-stu-id="ba4fe-117">If `wszTextOut` is not null, the function stores text in `wszTextOut` up to the location indicated by `puiTextLength`.</span></span> <span data-ttu-id="ba4fe-118">Ele retorna com êxito se havia espaço suficiente no buffer ou retorna E_OUTOFMEMORY se o buffer não era longo o suficiente.</span><span class="sxs-lookup"><span data-stu-id="ba4fe-118">It returns successfully if there was enough room in the buffer, or returns E_OUTOFMEMORY if the buffer was not long enough.</span></span>  
  
- <span data-ttu-id="ba4fe-119">A parte de transição da função será ignorada se `pTransitionContexts` e `puiTransitionContextCount` forem nulos.</span><span class="sxs-lookup"><span data-stu-id="ba4fe-119">The transition portion of the function is ignored if `pTransitionContexts` and `puiTransitionContextCount` are both null.</span></span> <span data-ttu-id="ba4fe-120">Nesse caso, a função fornece chamadores com a saída de texto apenas dos nomes de função.</span><span class="sxs-lookup"><span data-stu-id="ba4fe-120">In this case, the function provides callers with text output of only the function names.</span></span>  
  
- <span data-ttu-id="ba4fe-121">Se `pTransitionContexts` for NULL e `puiTransitionContextCount` não for NULL, a função retornará o número necessário de entradas de contexto em `puiTransitionContextCount`.</span><span class="sxs-lookup"><span data-stu-id="ba4fe-121">If `pTransitionContexts` is null and `puiTransitionContextCount` is not null, the function returns the necessary number of context entries in `puiTransitionContextCount`.</span></span>  
  
- <span data-ttu-id="ba4fe-122">Se `pTransitionContexts` não for NULL, a função o tratará como uma matriz de estruturas de comprimento `puiTransitionContextCount`.</span><span class="sxs-lookup"><span data-stu-id="ba4fe-122">If `pTransitionContexts` is not null, the function treats it as an array of structures of length `puiTransitionContextCount`.</span></span> <span data-ttu-id="ba4fe-123">O tamanho da estrutura é fornecido por `uiSizeOfContext`e deve ser o tamanho de [SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) ou `CONTEXT` para a arquitetura.</span><span class="sxs-lookup"><span data-stu-id="ba4fe-123">The structure size is given by `uiSizeOfContext`, and must be the size of [SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) or `CONTEXT` for the architecture.</span></span>  
  
- <span data-ttu-id="ba4fe-124">`wszTextOut` é gravado no seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="ba4fe-124">`wszTextOut` is written in the following format:</span></span>  
  
    ```output  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
- <span data-ttu-id="ba4fe-125">Se o deslocamento em Hex for 0x0, nenhum deslocamento será gravado.</span><span class="sxs-lookup"><span data-stu-id="ba4fe-125">If the offset in hex is 0x0, no offset is written.</span></span>  
  
- <span data-ttu-id="ba4fe-126">Se não houver nenhum código gerenciado no thread atualmente no contexto, a função retornará SOS_E_NOMANAGEDCODE.</span><span class="sxs-lookup"><span data-stu-id="ba4fe-126">If there is no managed code on the thread currently in context, the function returns SOS_E_NOMANAGEDCODE.</span></span>  
  
- <span data-ttu-id="ba4fe-127">O parâmetro `Flags` é 0 ou SOS_STACKTRACE_SHOWADDRESSES para ver EBP e ESP na frente de cada linha de `module!functionname`.</span><span class="sxs-lookup"><span data-stu-id="ba4fe-127">The `Flags` parameter is either 0 or SOS_STACKTRACE_SHOWADDRESSES to see EBP and ESP in front of each `module!functionname` line.</span></span> <span data-ttu-id="ba4fe-128">Por padrão, é 0.</span><span class="sxs-lookup"><span data-stu-id="ba4fe-128">By default, it is 0.</span></span>  
  
    ```cpp  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a><span data-ttu-id="ba4fe-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ba4fe-129">Requirements</span></span>  
 <span data-ttu-id="ba4fe-130">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba4fe-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba4fe-131">**Cabeçalho:** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="ba4fe-131">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="ba4fe-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba4fe-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba4fe-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba4fe-133">See also</span></span>

- [<span data-ttu-id="ba4fe-134">Depurando funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="ba4fe-134">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
