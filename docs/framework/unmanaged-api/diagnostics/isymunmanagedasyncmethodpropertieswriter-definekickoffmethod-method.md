---
title: Método ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a476d92486d7f2523dfbcc8b25e9c11e26c55f2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="66dd0-102">Método ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod</span><span class="sxs-lookup"><span data-stu-id="66dd0-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="66dd0-103">Define o método inicial que inicia a operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="66dd0-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66dd0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="66dd0-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="66dd0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="66dd0-105">Parameters</span></span>  
  
|<span data-ttu-id="66dd0-106">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="66dd0-106">Parameter</span></span>|<span data-ttu-id="66dd0-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="66dd0-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="66dd0-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="66dd0-108">Return Value</span></span>  
 <span data-ttu-id="66dd0-109">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="66dd0-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66dd0-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="66dd0-110">Requirements</span></span>  
 <span data-ttu-id="66dd0-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="66dd0-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66dd0-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="66dd0-112">See Also</span></span>  
 [<span data-ttu-id="66dd0-113">Interface ISymUnmanagedAsyncMethodPropertiesWriter</span><span class="sxs-lookup"><span data-stu-id="66dd0-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
