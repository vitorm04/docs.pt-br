---
title: "Método ICeeGen::GetString"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICeeGen.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetString
helpviewer_keywords:
- ICeeGen::GetString method [.NET Framework metadata]
- GetString method, ICeeGen interface [.NET Framework metadata]
ms.assetid: 7cc22562-128c-440a-9147-55ff20f173d7
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7365cb96021438d9c7e287463782e1cb112a66a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="dbed0-102">Método ICeeGen::GetString</span><span class="sxs-lookup"><span data-stu-id="dbed0-102">ICeeGen::GetString Method</span></span>
<span data-ttu-id="dbed0-103">Obtém a cadeia de caracteres armazenada no endereço virtual relativo especificado.</span><span class="sxs-lookup"><span data-stu-id="dbed0-103">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="dbed0-104">Esse método está obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="dbed0-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbed0-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dbed0-105">Syntax</span></span>  
  
```  
HRESULT GetString (  
    [in]  ULONG      RVA,   
    [out] LPWSTR     *lpString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dbed0-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dbed0-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="dbed0-107">[in] O endereço virtual relativo da cadeia de caracteres para retornar.</span><span class="sxs-lookup"><span data-stu-id="dbed0-107">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="dbed0-108">[out] A cadeia de caracteres retornada.</span><span class="sxs-lookup"><span data-stu-id="dbed0-108">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbed0-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dbed0-109">Requirements</span></span>  
 <span data-ttu-id="dbed0-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbed0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbed0-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dbed0-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dbed0-112">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="dbed0-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dbed0-113">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbed0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbed0-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dbed0-114">See Also</span></span>  
 [<span data-ttu-id="dbed0-115">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="dbed0-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
