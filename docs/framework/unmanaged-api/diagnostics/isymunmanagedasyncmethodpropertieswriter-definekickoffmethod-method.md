---
title: Método ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38b4564aeb3c8ed4674e755e5691bb0a9d417bca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624148"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="e58d2-102">Método ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod</span><span class="sxs-lookup"><span data-stu-id="e58d2-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="e58d2-103">Define o método inicial que inicia a operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="e58d2-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e58d2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e58d2-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e58d2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e58d2-105">Parameters</span></span>  
  
|<span data-ttu-id="e58d2-106">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="e58d2-106">Parameter</span></span>|<span data-ttu-id="e58d2-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e58d2-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="e58d2-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e58d2-108">Return Value</span></span>  
 <span data-ttu-id="e58d2-109">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="e58d2-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e58d2-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e58d2-110">Requirements</span></span>  
 <span data-ttu-id="e58d2-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e58d2-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e58d2-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e58d2-112">See also</span></span>
- [<span data-ttu-id="e58d2-113">Interface ISymUnmanagedAsyncMethodPropertiesWriter</span><span class="sxs-lookup"><span data-stu-id="e58d2-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
