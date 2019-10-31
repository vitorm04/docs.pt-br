---
title: Método ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
ms.openlocfilehash: ccf1287a1b0218e7f2560e1afbb0930c93b43263
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129167"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="64102-102">Método ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod</span><span class="sxs-lookup"><span data-stu-id="64102-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="64102-103">Define o método inicial que inicia a operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="64102-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64102-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="64102-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64102-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="64102-105">Parameters</span></span>  
  
|<span data-ttu-id="64102-106">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="64102-106">Parameter</span></span>|<span data-ttu-id="64102-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="64102-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="64102-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="64102-108">Return Value</span></span>  
 <span data-ttu-id="64102-109">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="64102-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64102-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="64102-110">Requirements</span></span>  
 <span data-ttu-id="64102-111">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="64102-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64102-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64102-112">See also</span></span>

- [<span data-ttu-id="64102-113">Interface ISymUnmanagedAsyncMethodPropertiesWriter</span><span class="sxs-lookup"><span data-stu-id="64102-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
