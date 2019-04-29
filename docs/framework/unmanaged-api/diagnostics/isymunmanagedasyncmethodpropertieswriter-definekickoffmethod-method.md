---
title: Método ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce3c135e031d0c8425e990811fedc40f4ec45243
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940108"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="262d0-102">Método ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod</span><span class="sxs-lookup"><span data-stu-id="262d0-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="262d0-103">Define o método inicial que inicia a operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="262d0-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="262d0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="262d0-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="262d0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="262d0-105">Parameters</span></span>  
  
|<span data-ttu-id="262d0-106">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="262d0-106">Parameter</span></span>|<span data-ttu-id="262d0-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="262d0-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="262d0-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="262d0-108">Return Value</span></span>  
 <span data-ttu-id="262d0-109">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="262d0-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="262d0-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="262d0-110">Requirements</span></span>  
 <span data-ttu-id="262d0-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="262d0-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="262d0-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="262d0-112">See also</span></span>

- [<span data-ttu-id="262d0-113">Interface ISymUnmanagedAsyncMethodPropertiesWriter</span><span class="sxs-lookup"><span data-stu-id="262d0-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
