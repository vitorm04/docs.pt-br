---
title: Função CloseCLREnumeration
ms.date: 03/30/2017
api_name:
- CloseCLREnumeration
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- CloseCLREnumeration
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CloseCLR Enumeration function
ms.assetid: 5e3c3958-80bb-43b1-a96b-dd3e6dbd9cd7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a05a779d4a56eb8f881da1824d5ffaa363b5a01
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274275"
---
# <a name="closeclrenumeration-function"></a><span data-ttu-id="b1bc8-102">Função CloseCLREnumeration</span><span class="sxs-lookup"><span data-stu-id="b1bc8-102">CloseCLREnumeration Function</span></span>
<span data-ttu-id="b1bc8-103">Fecha os eventos de inicialização de continuação de Common Language Runtime (CLR) válidos localizados em uma matriz de identificadores retornada pela [função EnumerateCLRs](enumerateclrs-function.md)e libera a memória para as matrizes de caminho de cadeia de caracteres e identificador.</span><span class="sxs-lookup"><span data-stu-id="b1bc8-103">Closes any valid common language runtime (CLR) continue-startup events located in an array of handles returned by the [EnumerateCLRs function](enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1bc8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b1bc8-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1bc8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b1bc8-105">Parameters</span></span>  
 `pHandleArray`  
 <span data-ttu-id="b1bc8-106">no Ponteiro para a matriz de identificadores de eventos retornados da [função EnumerateCLRs](enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="b1bc8-106">[in] Pointer to the array of event handles returned from the [EnumerateCLRs function](enumerateclrs-function.md).</span></span>  
  
 `pStringArray`  
 <span data-ttu-id="b1bc8-107">no Ponteiro para a matriz de caminhos de cadeia de caracteres CLR retornados da [função EnumerateCLRs](enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="b1bc8-107">[in] Pointer to the array of CLR string paths returned from the [EnumerateCLRs function](enumerateclrs-function.md).</span></span>  
  
 `dwArrayLength`  
 <span data-ttu-id="b1bc8-108">no DWORD que contém o tamanho (comprimento) de `pHandleArray` ou `pStringArray` (eles são os mesmos).</span><span class="sxs-lookup"><span data-stu-id="b1bc8-108">[in] DWORD that contains the size (length) of either `pHandleArray` or `pStringArray` (they are the same).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1bc8-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b1bc8-109">Return Value</span></span>  
 <span data-ttu-id="b1bc8-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b1bc8-110">S_OK</span></span>  
 <span data-ttu-id="b1bc8-111">Os identificadores abertos pela [função EnumerateCLRs](enumerateclrs-function.md) são fechados e a memória alocada para o identificador e as matrizes de cadeia de caracteres é liberada.</span><span class="sxs-lookup"><span data-stu-id="b1bc8-111">Handles opened by the [EnumerateCLRs function](enumerateclrs-function.md) are closed, and memory allocated for the handle and string arrays is freed.</span></span>  
  
 <span data-ttu-id="b1bc8-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b1bc8-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="b1bc8-113">O comprimento de `pHandleArray` não corresponde ao comprimento `dwArrayLength`passado.</span><span class="sxs-lookup"><span data-stu-id="b1bc8-113">The length of `pHandleArray` does not match the length that is passed in `dwArrayLength`.</span></span>  
  
 <span data-ttu-id="b1bc8-114">E_FAIL (ou outros códigos de retorno de E_)</span><span class="sxs-lookup"><span data-stu-id="b1bc8-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="b1bc8-115">A função não pode liberar a memória para `pHandleArray` e. `pStringArray`</span><span class="sxs-lookup"><span data-stu-id="b1bc8-115">The function is unable to free the memory for `pHandleArray` and `pStringArray`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1bc8-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b1bc8-116">Requirements</span></span>  
 <span data-ttu-id="b1bc8-117">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1bc8-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1bc8-118">**Cabeçalho:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="b1bc8-118">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="b1bc8-119">**Biblioteca:** dbgshim. dll</span><span class="sxs-lookup"><span data-stu-id="b1bc8-119">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="b1bc8-120">**.NET Framework versões:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="b1bc8-120">**.NET Framework Versions:** 3.5 SP1</span></span>
