---
title: Método ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo
ms.date: 03/30/2017
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a8305d0a562fd90e3fae32e372b663ca3942d2a4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080846"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="d756c-102">Método ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo</span><span class="sxs-lookup"><span data-stu-id="d756c-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>
<span data-ttu-id="d756c-103">Definir um grupo de async await operações no método atual.</span><span class="sxs-lookup"><span data-stu-id="d756c-103">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="d756c-104">Cada deslocamento yield corresponde à instrução de retorno de uma expressão await, identificando um potencial yield.</span><span class="sxs-lookup"><span data-stu-id="d756c-104">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="d756c-105">Cada `breakpointMethod` / `breakpointOffset` par nos informa onde a operação assíncrona será retomada que pode estar em um método diferente.</span><span class="sxs-lookup"><span data-stu-id="d756c-105">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d756c-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d756c-106">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d756c-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d756c-107">Parameters</span></span>  
  
|<span data-ttu-id="d756c-108">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="d756c-108">Parameter</span></span>|<span data-ttu-id="d756c-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="d756c-109">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="d756c-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d756c-110">Return Value</span></span>  
 <span data-ttu-id="d756c-111">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="d756c-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d756c-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d756c-112">Requirements</span></span>  
 <span data-ttu-id="d756c-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d756c-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d756c-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d756c-114">See also</span></span>

- [<span data-ttu-id="d756c-115">Interface ISymUnmanagedAsyncMethodPropertiesWriter</span><span class="sxs-lookup"><span data-stu-id="d756c-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
