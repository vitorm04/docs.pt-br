---
title: Método ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo
ms.date: 03/30/2017
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
ms.openlocfilehash: 5a501cca16f06e7ccd5da9f65a213c6b24c1092c
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441780"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="797ee-102">Método ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo</span><span class="sxs-lookup"><span data-stu-id="797ee-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>
<span data-ttu-id="797ee-103">Defina um grupo de operações assíncronas Await no método atual.</span><span class="sxs-lookup"><span data-stu-id="797ee-103">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="797ee-104">Cada deslocamento de rendimento corresponde a uma instrução de retorno de Await, identificando um possível rendimento.</span><span class="sxs-lookup"><span data-stu-id="797ee-104">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="797ee-105">Cada `breakpointMethod` / `breakpointOffset` par informa onde a operação assíncrona será retomada, o que pode estar em um método diferente.</span><span class="sxs-lookup"><span data-stu-id="797ee-105">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="797ee-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="797ee-106">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="797ee-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="797ee-107">Parameters</span></span>  
  
|<span data-ttu-id="797ee-108">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="797ee-108">Parameter</span></span>|<span data-ttu-id="797ee-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="797ee-109">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="797ee-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="797ee-110">Return Value</span></span>  
 <span data-ttu-id="797ee-111">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="797ee-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="797ee-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="797ee-112">Requirements</span></span>  
 <span data-ttu-id="797ee-113">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="797ee-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="797ee-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="797ee-114">See also</span></span>

- [<span data-ttu-id="797ee-115">Interface ISymUnmanagedAsyncMethodPropertiesWriter</span><span class="sxs-lookup"><span data-stu-id="797ee-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)
