---
title: "Função CloseCLREnumeration"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CloseCLREnumeration
api_location: dbgshim.dll
api_type: COM
f1_keywords: CloseCLREnumeration
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CloseCLR Enumeration function
ms.assetid: 5e3c3958-80bb-43b1-a96b-dd3e6dbd9cd7
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d9f14b851795c92c3ce0c1e7536a4ff78fbdf927
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="closeclrenumeration-function"></a><span data-ttu-id="96754-102">Função CloseCLREnumeration</span><span class="sxs-lookup"><span data-stu-id="96754-102">CloseCLREnumeration Function</span></span>
<span data-ttu-id="96754-103">Fecha qualquer válido language runtime (CLR) inicialização continuar eventos comuns localizados em uma matriz de identificadores retornado pelo [função EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)e libera a memória para as matrizes de caminho do identificador e a cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="96754-103">Closes any valid common language runtime (CLR) continue-startup events located in an array of handles returned by the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96754-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="96754-104">Syntax</span></span>  
  
```  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="96754-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="96754-105">Parameters</span></span>  
 `pHandleArray`  
 <span data-ttu-id="96754-106">[in] Ponteiro para a matriz de identificadores de eventos retornado do [função EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="96754-106">[in] Pointer to the array of event handles returned from the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span></span>  
  
 `pStringArray`  
 <span data-ttu-id="96754-107">[in] Ponteiro para a matriz de caminhos de cadeia de caracteres CLR retornado do [função EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="96754-107">[in] Pointer to the array of CLR string paths returned from the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span></span>  
  
 `dwArrayLength`  
 <span data-ttu-id="96754-108">[in] DWORD que contém o tamanho (comprimento) do `pHandleArray` ou `pStringArray` (eles são os mesmos).</span><span class="sxs-lookup"><span data-stu-id="96754-108">[in] DWORD that contains the size (length) of either `pHandleArray` or `pStringArray` (they are the same).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="96754-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="96754-109">Return Value</span></span>  
 <span data-ttu-id="96754-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="96754-110">S_OK</span></span>  
 <span data-ttu-id="96754-111">Identificadores abertos pelo [função EnumerateCLRs](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md) são fechadas, e a memória alocada para as matrizes de identificador e a cadeia de caracteres é liberada.</span><span class="sxs-lookup"><span data-stu-id="96754-111">Handles opened by the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md) are closed, and memory allocated for the handle and string arrays is freed.</span></span>  
  
 <span data-ttu-id="96754-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="96754-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="96754-113">O comprimento de `pHandleArray` não corresponde ao tamanho que é transmitido `dwArrayLength`.</span><span class="sxs-lookup"><span data-stu-id="96754-113">The length of `pHandleArray` does not match the length that is passed in `dwArrayLength`.</span></span>  
  
 <span data-ttu-id="96754-114">E_FAIL (ou outros códigos de retorno E_)</span><span class="sxs-lookup"><span data-stu-id="96754-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="96754-115">A função é não é possível liberar a memória para `pHandleArray` e `pStringArray`.</span><span class="sxs-lookup"><span data-stu-id="96754-115">The function is unable to free the memory for `pHandleArray` and `pStringArray`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96754-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="96754-116">Requirements</span></span>  
 <span data-ttu-id="96754-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96754-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96754-118">**Cabeçalho:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="96754-118">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="96754-119">**Biblioteca:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="96754-119">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="96754-120">**Versões do .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="96754-120">**.NET Framework Versions:** 3.5 SP1</span></span>
