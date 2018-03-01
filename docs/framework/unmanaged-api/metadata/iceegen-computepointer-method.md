---
title: "Método ICeeGen::ComputePointer"
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
- ICeeGen.ComputePointer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::ComputePointer
helpviewer_keywords:
- ICeeGen::ComputePointer method [.NET Framework metadata]
- ComputePointer method [.NET Framework metadata]
ms.assetid: b6b95c04-0f2c-4fcc-a8bc-3b1dcbdba731
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0b027615f7697b9ea103d44bea0ec44834fe3f04
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="1ea08-102">Método ICeeGen::ComputePointer</span><span class="sxs-lookup"><span data-stu-id="1ea08-102">ICeeGen::ComputePointer Method</span></span>
<span data-ttu-id="1ea08-103">Determina o buffer para a seção de código especificada.</span><span class="sxs-lookup"><span data-stu-id="1ea08-103">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="1ea08-104">Esse método está obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="1ea08-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ea08-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1ea08-105">Syntax</span></span>  
  
```  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,   
    [out] UCHAR        **lpBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1ea08-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1ea08-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="1ea08-107">[in] A seção de código para o qual retornar um buffer.</span><span class="sxs-lookup"><span data-stu-id="1ea08-107">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="1ea08-108">[in] O endereço virtual relativo do método para o qual obter um ponteiro.</span><span class="sxs-lookup"><span data-stu-id="1ea08-108">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="1ea08-109">[out] Um ponteiro para o buffer retornado.</span><span class="sxs-lookup"><span data-stu-id="1ea08-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ea08-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1ea08-110">Requirements</span></span>  
 <span data-ttu-id="1ea08-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ea08-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ea08-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1ea08-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1ea08-113">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="1ea08-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1ea08-114">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ea08-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ea08-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ea08-115">See Also</span></span>  
 [<span data-ttu-id="1ea08-116">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="1ea08-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
