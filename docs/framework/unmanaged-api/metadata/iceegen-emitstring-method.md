---
title: Método ICeeGen::EmitString
ms.date: 03/30/2017
api_name:
- ICeeGen.EmitString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::EmitString
helpviewer_keywords:
- EmitString method [.NET Framework metadata]
- ICeeGen::EmitString method [.NET Framework metadata]
ms.assetid: ad2710a7-edb8-4493-8619-3fce235e3334
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1eabf5631fcfe7a187d0e203d64c7a7f4f5a819a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209951"
---
# <a name="iceegenemitstring-method"></a><span data-ttu-id="b1387-102">Método ICeeGen::EmitString</span><span class="sxs-lookup"><span data-stu-id="b1387-102">ICeeGen::EmitString Method</span></span>
<span data-ttu-id="b1387-103">Emite a cadeia de caracteres especificada para a base de código.</span><span class="sxs-lookup"><span data-stu-id="b1387-103">Emits the specified string into the code base.</span></span>  
  
 <span data-ttu-id="b1387-104">Esse método é obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="b1387-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1387-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b1387-105">Syntax</span></span>  
  
```  
HRESULT EmitString (  
    [in]  LPWSTR    lpString,  
    [out] ULONG     *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1387-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b1387-106">Parameters</span></span>  
 `lpString`  
 <span data-ttu-id="b1387-107">[in] A cadeia de caracteres para emitir.</span><span class="sxs-lookup"><span data-stu-id="b1387-107">[in] The string to emit.</span></span>  
  
 `RVA`  
 <span data-ttu-id="b1387-108">[out] O endereço virtual relativo da cadeia de caracteres emitido.</span><span class="sxs-lookup"><span data-stu-id="b1387-108">[out] The relative virtual address of the emitted string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1387-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b1387-109">Requirements</span></span>  
 <span data-ttu-id="b1387-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1387-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1387-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b1387-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b1387-112">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="b1387-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="b1387-113">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="b1387-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b1387-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1387-114">See also</span></span>

- [<span data-ttu-id="b1387-115">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="b1387-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
