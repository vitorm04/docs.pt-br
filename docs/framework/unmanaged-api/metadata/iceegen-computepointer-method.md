---
title: Método ICeeGen::ComputePointer
ms.date: 03/30/2017
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
ms.openlocfilehash: 206dcd3a0a82da9b6211c8c2045e4e9d3d991973
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008866"
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="a8958-102">Método ICeeGen::ComputePointer</span><span class="sxs-lookup"><span data-stu-id="a8958-102">ICeeGen::ComputePointer Method</span></span>
<span data-ttu-id="a8958-103">Determina o buffer para a seção de código especificada.</span><span class="sxs-lookup"><span data-stu-id="a8958-103">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="a8958-104">Este método é obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="a8958-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8958-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a8958-105">Syntax</span></span>  
  
```cpp  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,
    [out] UCHAR        **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8958-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a8958-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="a8958-107">no A seção de código para a qual retornar um buffer.</span><span class="sxs-lookup"><span data-stu-id="a8958-107">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="a8958-108">no O endereço virtual relativo do método para o qual obter um ponteiro.</span><span class="sxs-lookup"><span data-stu-id="a8958-108">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="a8958-109">fora Um ponteiro para o buffer retornado.</span><span class="sxs-lookup"><span data-stu-id="a8958-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8958-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a8958-110">Requirements</span></span>  
 <span data-ttu-id="a8958-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8958-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8958-112">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a8958-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a8958-113">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a8958-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a8958-114">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8958-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8958-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="a8958-115">See also</span></span>

- [<span data-ttu-id="a8958-116">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="a8958-116">ICeeGen Interface</span></span>](iceegen-interface.md)
