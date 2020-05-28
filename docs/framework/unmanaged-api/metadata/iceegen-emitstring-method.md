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
ms.openlocfilehash: e7c58e6cdbe0d3c8513721a40eaa3fdfcec6ce2e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008853"
---
# <a name="iceegenemitstring-method"></a><span data-ttu-id="dba20-102">Método ICeeGen::EmitString</span><span class="sxs-lookup"><span data-stu-id="dba20-102">ICeeGen::EmitString Method</span></span>
<span data-ttu-id="dba20-103">Emite a cadeia de caracteres especificada na base de código.</span><span class="sxs-lookup"><span data-stu-id="dba20-103">Emits the specified string into the code base.</span></span>  
  
 <span data-ttu-id="dba20-104">Este método é obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="dba20-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dba20-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dba20-105">Syntax</span></span>  
  
```cpp  
HRESULT EmitString (  
    [in]  LPWSTR    lpString,  
    [out] ULONG     *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dba20-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dba20-106">Parameters</span></span>  
 `lpString`  
 <span data-ttu-id="dba20-107">no A cadeia de caracteres a ser emitida.</span><span class="sxs-lookup"><span data-stu-id="dba20-107">[in] The string to emit.</span></span>  
  
 `RVA`  
 <span data-ttu-id="dba20-108">fora O endereço virtual relativo da cadeia de caracteres emitida.</span><span class="sxs-lookup"><span data-stu-id="dba20-108">[out] The relative virtual address of the emitted string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dba20-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dba20-109">Requirements</span></span>  
 <span data-ttu-id="dba20-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dba20-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dba20-111">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="dba20-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dba20-112">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="dba20-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dba20-113">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dba20-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dba20-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="dba20-114">See also</span></span>

- [<span data-ttu-id="dba20-115">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="dba20-115">ICeeGen Interface</span></span>](iceegen-interface.md)
