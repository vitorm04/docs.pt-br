---
title: Método ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
ms.openlocfilehash: c35455fc679d79d56814a9c2f026ec395e944f24
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441715"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="4de38-102">Método ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod</span><span class="sxs-lookup"><span data-stu-id="4de38-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="4de38-103">Define o método inicial que inicia a operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="4de38-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4de38-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4de38-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4de38-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4de38-105">Parameters</span></span>  
  
|<span data-ttu-id="4de38-106">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="4de38-106">Parameter</span></span>|<span data-ttu-id="4de38-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="4de38-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="4de38-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="4de38-108">Return Value</span></span>  
 <span data-ttu-id="4de38-109">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="4de38-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4de38-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4de38-110">Requirements</span></span>  
 <span data-ttu-id="4de38-111">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4de38-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4de38-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="4de38-112">See also</span></span>

- [<span data-ttu-id="4de38-113">Interface ISymUnmanagedAsyncMethodPropertiesWriter</span><span class="sxs-lookup"><span data-stu-id="4de38-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)
