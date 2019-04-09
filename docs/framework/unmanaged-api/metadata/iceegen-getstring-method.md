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
ms.openlocfilehash: 70d78942d4db2fea2cc1ccbcc5ddb20d743e9fdf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093664"
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="b22eb-102">Método ICeeGen::GetString</span><span class="sxs-lookup"><span data-stu-id="b22eb-102">ICeeGen::GetString Method</span></span>
<span data-ttu-id="b22eb-103">Obtém a cadeia de caracteres armazenada no endereço virtual relativo especificado.</span><span class="sxs-lookup"><span data-stu-id="b22eb-103">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="b22eb-104">Esse método é obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="b22eb-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b22eb-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b22eb-105">Syntax</span></span>  
  
```  
HRESULT GetString (  
    [in]  ULONG      RVA,   
    [out] LPWSTR     *lpString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b22eb-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b22eb-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="b22eb-107">[in] O endereço virtual relativo da cadeia de caracteres para retornar.</span><span class="sxs-lookup"><span data-stu-id="b22eb-107">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="b22eb-108">[out] Cadeia de caracteres retornada.</span><span class="sxs-lookup"><span data-stu-id="b22eb-108">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b22eb-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b22eb-109">Requirements</span></span>  
 <span data-ttu-id="b22eb-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b22eb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b22eb-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b22eb-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b22eb-112">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="b22eb-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="b22eb-113">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="b22eb-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b22eb-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b22eb-114">See also</span></span>

- [<span data-ttu-id="b22eb-115">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="b22eb-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
