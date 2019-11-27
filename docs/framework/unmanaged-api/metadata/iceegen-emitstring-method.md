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
ms.openlocfilehash: 8433ff6e0ec550d6b0558bfb9c7698c49e98278c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436390"
---
# <a name="iceegenemitstring-method"></a><span data-ttu-id="adc9e-102">Método ICeeGen::EmitString</span><span class="sxs-lookup"><span data-stu-id="adc9e-102">ICeeGen::EmitString Method</span></span>
<span data-ttu-id="adc9e-103">Emite a cadeia de caracteres especificada na base de código.</span><span class="sxs-lookup"><span data-stu-id="adc9e-103">Emits the specified string into the code base.</span></span>  
  
 <span data-ttu-id="adc9e-104">Este método é obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="adc9e-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adc9e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="adc9e-105">Syntax</span></span>  
  
```cpp  
HRESULT EmitString (  
    [in]  LPWSTR    lpString,  
    [out] ULONG     *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="adc9e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="adc9e-106">Parameters</span></span>  
 `lpString`  
 <span data-ttu-id="adc9e-107">no A cadeia de caracteres a ser emitida.</span><span class="sxs-lookup"><span data-stu-id="adc9e-107">[in] The string to emit.</span></span>  
  
 `RVA`  
 <span data-ttu-id="adc9e-108">fora O endereço virtual relativo da cadeia de caracteres emitida.</span><span class="sxs-lookup"><span data-stu-id="adc9e-108">[out] The relative virtual address of the emitted string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="adc9e-109">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="adc9e-109">Requirements</span></span>  
 <span data-ttu-id="adc9e-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="adc9e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adc9e-111">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="adc9e-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="adc9e-112">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="adc9e-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="adc9e-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adc9e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adc9e-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="adc9e-114">See also</span></span>

- [<span data-ttu-id="adc9e-115">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="adc9e-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
