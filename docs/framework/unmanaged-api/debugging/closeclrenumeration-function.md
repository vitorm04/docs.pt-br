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
ms.openlocfilehash: 1d42292705dae03e9bf1a1555508dfb69cebde82
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132431"
---
# <a name="closeclrenumeration-function"></a><span data-ttu-id="8f8d6-102">Função CloseCLREnumeration</span><span class="sxs-lookup"><span data-stu-id="8f8d6-102">CloseCLREnumeration Function</span></span>
<span data-ttu-id="8f8d6-103">Fecha os eventos de inicialização de continuação de Common Language Runtime (CLR) válidos localizados em uma matriz de identificadores retornada pela [função EnumerateCLRs](enumerateclrs-function.md)e libera a memória para as matrizes de caminho de cadeia de caracteres e identificador.</span><span class="sxs-lookup"><span data-stu-id="8f8d6-103">Closes any valid common language runtime (CLR) continue-startup events located in an array of handles returned by the [EnumerateCLRs function](enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f8d6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8f8d6-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f8d6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8f8d6-105">Parameters</span></span>  
 `pHandleArray`  
 <span data-ttu-id="8f8d6-106">no Ponteiro para a matriz de identificadores de eventos retornados da [função EnumerateCLRs](enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="8f8d6-106">[in] Pointer to the array of event handles returned from the [EnumerateCLRs function](enumerateclrs-function.md).</span></span>  
  
 `pStringArray`  
 <span data-ttu-id="8f8d6-107">no Ponteiro para a matriz de caminhos de cadeia de caracteres CLR retornados da [função EnumerateCLRs](enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="8f8d6-107">[in] Pointer to the array of CLR string paths returned from the [EnumerateCLRs function](enumerateclrs-function.md).</span></span>  
  
 `dwArrayLength`  
 <span data-ttu-id="8f8d6-108">no DWORD que contém o tamanho (comprimento) de `pHandleArray` ou `pStringArray` (eles são os mesmos).</span><span class="sxs-lookup"><span data-stu-id="8f8d6-108">[in] DWORD that contains the size (length) of either `pHandleArray` or `pStringArray` (they are the same).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f8d6-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="8f8d6-109">Return Value</span></span>  
 <span data-ttu-id="8f8d6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8f8d6-110">S_OK</span></span>  
 <span data-ttu-id="8f8d6-111">Os identificadores abertos pela [função EnumerateCLRs](enumerateclrs-function.md) são fechados e a memória alocada para o identificador e as matrizes de cadeia de caracteres é liberada.</span><span class="sxs-lookup"><span data-stu-id="8f8d6-111">Handles opened by the [EnumerateCLRs function](enumerateclrs-function.md) are closed, and memory allocated for the handle and string arrays is freed.</span></span>  
  
 <span data-ttu-id="8f8d6-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8f8d6-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="8f8d6-113">O comprimento de `pHandleArray` não corresponde ao comprimento passado na `dwArrayLength`.</span><span class="sxs-lookup"><span data-stu-id="8f8d6-113">The length of `pHandleArray` does not match the length that is passed in `dwArrayLength`.</span></span>  
  
 <span data-ttu-id="8f8d6-114">E_FAIL (ou outros códigos de retorno de E_)</span><span class="sxs-lookup"><span data-stu-id="8f8d6-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="8f8d6-115">A função não pode liberar a memória para `pHandleArray` e `pStringArray`.</span><span class="sxs-lookup"><span data-stu-id="8f8d6-115">The function is unable to free the memory for `pHandleArray` and `pStringArray`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f8d6-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8f8d6-116">Requirements</span></span>  
 <span data-ttu-id="8f8d6-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f8d6-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f8d6-118">**Cabeçalho:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="8f8d6-118">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="8f8d6-119">**Biblioteca:** dbgshim. dll</span><span class="sxs-lookup"><span data-stu-id="8f8d6-119">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="8f8d6-120">**Versões do .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="8f8d6-120">**.NET Framework Versions:** 3.5 SP1</span></span>
