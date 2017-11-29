---
title: "Método ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 68c5d6662d8cbecca06268bd5010878c4e476f47
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="27375-102">Método ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod</span><span class="sxs-lookup"><span data-stu-id="27375-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="27375-103">Define o método inicial que inicia a operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="27375-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27375-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="27375-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="27375-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="27375-105">Parameters</span></span>  
  
|<span data-ttu-id="27375-106">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="27375-106">Parameter</span></span>|<span data-ttu-id="27375-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="27375-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="27375-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="27375-108">Return Value</span></span>  
 <span data-ttu-id="27375-109">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="27375-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27375-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="27375-110">Requirements</span></span>  
 <span data-ttu-id="27375-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="27375-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27375-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27375-112">See Also</span></span>  
 [<span data-ttu-id="27375-113">Interface ISymUnmanagedAsyncMethodPropertiesWriter</span><span class="sxs-lookup"><span data-stu-id="27375-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
