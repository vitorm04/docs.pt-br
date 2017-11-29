---
title: "Método ICeeGen::EmitString"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.EmitString
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::EmitString
helpviewer_keywords:
- EmitString method [.NET Framework metadata]
- ICeeGen::EmitString method [.NET Framework metadata]
ms.assetid: ad2710a7-edb8-4493-8619-3fce235e3334
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f988e54a37212beeeebfbef15e6b148021e0b759
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="iceegenemitstring-method"></a><span data-ttu-id="3a73e-102">Método ICeeGen::EmitString</span><span class="sxs-lookup"><span data-stu-id="3a73e-102">ICeeGen::EmitString Method</span></span>
<span data-ttu-id="3a73e-103">Emite a cadeia de caracteres especificada para a base de código.</span><span class="sxs-lookup"><span data-stu-id="3a73e-103">Emits the specified string into the code base.</span></span>  
  
 <span data-ttu-id="3a73e-104">Esse método está obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="3a73e-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a73e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3a73e-105">Syntax</span></span>  
  
```  
HRESULT EmitString (  
    [in]  LPWSTR    lpString,  
    [out] ULONG     *RVA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3a73e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3a73e-106">Parameters</span></span>  
 `lpString`  
 <span data-ttu-id="3a73e-107">[in] A cadeia de caracteres de emissão.</span><span class="sxs-lookup"><span data-stu-id="3a73e-107">[in] The string to emit.</span></span>  
  
 `RVA`  
 <span data-ttu-id="3a73e-108">[out] O endereço virtual relativo da cadeia de caracteres emitido.</span><span class="sxs-lookup"><span data-stu-id="3a73e-108">[out] The relative virtual address of the emitted string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a73e-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3a73e-109">Requirements</span></span>  
 <span data-ttu-id="3a73e-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a73e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a73e-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3a73e-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3a73e-112">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="3a73e-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3a73e-113">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a73e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a73e-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3a73e-114">See Also</span></span>  
 [<span data-ttu-id="3a73e-115">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="3a73e-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
