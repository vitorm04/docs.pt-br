---
title: Método ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo
ms.date: 03/30/2017
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
ms.openlocfilehash: 59e3a95a4d2573263600da60b4f852caa361138e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129195"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="ae60a-102">Método ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo</span><span class="sxs-lookup"><span data-stu-id="ae60a-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>
<span data-ttu-id="ae60a-103">Defina um grupo de operações assíncronas Await no método atual.</span><span class="sxs-lookup"><span data-stu-id="ae60a-103">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="ae60a-104">Cada deslocamento de rendimento corresponde a uma instrução de retorno de Await, identificando um possível rendimento.</span><span class="sxs-lookup"><span data-stu-id="ae60a-104">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="ae60a-105">Cada `breakpointMethod`/par `breakpointOffset` nos informa onde a operação assíncrona retomará, o que pode estar em um método diferente.</span><span class="sxs-lookup"><span data-stu-id="ae60a-105">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae60a-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ae60a-106">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae60a-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ae60a-107">Parameters</span></span>  
  
|<span data-ttu-id="ae60a-108">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="ae60a-108">Parameter</span></span>|<span data-ttu-id="ae60a-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="ae60a-109">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="ae60a-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="ae60a-110">Return Value</span></span>  
 <span data-ttu-id="ae60a-111">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="ae60a-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae60a-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ae60a-112">Requirements</span></span>  
 <span data-ttu-id="ae60a-113">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="ae60a-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae60a-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae60a-114">See also</span></span>

- [<span data-ttu-id="ae60a-115">Interface ISymUnmanagedAsyncMethodPropertiesWriter</span><span class="sxs-lookup"><span data-stu-id="ae60a-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
