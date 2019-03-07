---
title: Método ICeeGen::GetString
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bf3f781e23d0787d01a1ef04b41b2c38eaaa9e0d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479331"
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="ce697-102">Método ICeeGen::GetString</span><span class="sxs-lookup"><span data-stu-id="ce697-102">ICeeGen::GetString Method</span></span>
<span data-ttu-id="ce697-103">Obtém a cadeia de caracteres armazenada no endereço virtual relativo especificado.</span><span class="sxs-lookup"><span data-stu-id="ce697-103">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="ce697-104">Esse método é obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="ce697-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce697-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ce697-105">Syntax</span></span>  
  
```  
HRESULT GetString (  
    [in]  ULONG      RVA,   
    [out] LPWSTR     *lpString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce697-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ce697-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="ce697-107">[in] O endereço virtual relativo da cadeia de caracteres para retornar.</span><span class="sxs-lookup"><span data-stu-id="ce697-107">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="ce697-108">[out] Cadeia de caracteres retornada.</span><span class="sxs-lookup"><span data-stu-id="ce697-108">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce697-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ce697-109">Requirements</span></span>  
 <span data-ttu-id="ce697-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce697-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce697-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ce697-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ce697-112">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="ce697-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ce697-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce697-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce697-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce697-114">See also</span></span>
- [<span data-ttu-id="ce697-115">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="ce697-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
