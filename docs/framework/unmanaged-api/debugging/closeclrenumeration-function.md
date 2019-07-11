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
ms.openlocfilehash: a9eb9bb1e4abeb98d8d0ba2b052612d918c45f22
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741090"
---
# <a name="closeclrenumeration-function"></a><span data-ttu-id="544eb-102">Função CloseCLREnumeration</span><span class="sxs-lookup"><span data-stu-id="544eb-102">CloseCLREnumeration Function</span></span>
<span data-ttu-id="544eb-103">Fecha qualquer válido runtime (CLR) inicialização continuar eventos de common language localizados em uma matriz de identificadores retornado pela [função EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)e libera a memória para as matrizes de caminho do identificador e a cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="544eb-103">Closes any valid common language runtime (CLR) continue-startup events located in an array of handles returned by the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="544eb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="544eb-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="544eb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="544eb-105">Parameters</span></span>  
 `pHandleArray`  
 <span data-ttu-id="544eb-106">[in] Ponteiro para a matriz de identificadores de eventos retornados do [função EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="544eb-106">[in] Pointer to the array of event handles returned from the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span></span>  
  
 `pStringArray`  
 <span data-ttu-id="544eb-107">[in] Ponteiro para a matriz de caminhos de cadeia de caracteres CLR retornado do [função EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="544eb-107">[in] Pointer to the array of CLR string paths returned from the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span></span>  
  
 `dwArrayLength`  
 <span data-ttu-id="544eb-108">[in] Que contém o tamanho (comprimento) de um DWORD `pHandleArray` ou `pStringArray` (eles são iguais).</span><span class="sxs-lookup"><span data-stu-id="544eb-108">[in] DWORD that contains the size (length) of either `pHandleArray` or `pStringArray` (they are the same).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="544eb-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="544eb-109">Return Value</span></span>  
 <span data-ttu-id="544eb-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="544eb-110">S_OK</span></span>  
 <span data-ttu-id="544eb-111">Identificadores abertos pelo [função EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md) são fechados, e a memória alocada para as matrizes de cadeia de caracteres de identificador é liberada.</span><span class="sxs-lookup"><span data-stu-id="544eb-111">Handles opened by the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md) are closed, and memory allocated for the handle and string arrays is freed.</span></span>  
  
 <span data-ttu-id="544eb-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="544eb-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="544eb-113">O comprimento da `pHandleArray` não corresponde ao tamanho que é passado no `dwArrayLength`.</span><span class="sxs-lookup"><span data-stu-id="544eb-113">The length of `pHandleArray` does not match the length that is passed in `dwArrayLength`.</span></span>  
  
 <span data-ttu-id="544eb-114">E_FAIL (ou outros códigos de retorno e _)</span><span class="sxs-lookup"><span data-stu-id="544eb-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="544eb-115">A função não é possível liberar a memória para `pHandleArray` e `pStringArray`.</span><span class="sxs-lookup"><span data-stu-id="544eb-115">The function is unable to free the memory for `pHandleArray` and `pStringArray`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="544eb-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="544eb-116">Requirements</span></span>  
 <span data-ttu-id="544eb-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="544eb-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="544eb-118">**Cabeçalho:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="544eb-118">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="544eb-119">**Biblioteca:** dbgshim</span><span class="sxs-lookup"><span data-stu-id="544eb-119">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="544eb-120">**Versões do .NET framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="544eb-120">**.NET Framework Versions:** 3.5 SP1</span></span>
