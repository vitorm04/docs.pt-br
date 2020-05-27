---
title: Método ICeeGen::GetStringSection
ms.date: 03/30/2017
api_name:
- ICeeGen.GetStringSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetStringSection
helpviewer_keywords:
- ICeeGen::GetStringSection method [.NET Framework metadata]
- GetStringSection method [.NET Framework metadata]
ms.assetid: a2267d39-69d1-4de1-bf37-f752cafacc71
topic_type:
- apiref
ms.openlocfilehash: dbbfa77ee76770bcf1d662bc5ae179909eaf3b25
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008281"
---
# <a name="iceegengetstringsection-method"></a><span data-ttu-id="40eb8-102">Método ICeeGen::GetStringSection</span><span class="sxs-lookup"><span data-stu-id="40eb8-102">ICeeGen::GetStringSection Method</span></span>
<span data-ttu-id="40eb8-103">Obtém uma representação de cadeia de caracteres da seção de código referenciada pelo identificador especificado.</span><span class="sxs-lookup"><span data-stu-id="40eb8-103">Gets a string representation of the code section referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="40eb8-104">Este método é obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="40eb8-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40eb8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="40eb8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringSection (  
    [in, out] HCEESECTION     *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40eb8-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="40eb8-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="40eb8-107">[entrada, saída] O identificador para a seção de código.</span><span class="sxs-lookup"><span data-stu-id="40eb8-107">[in, out] The handle to the code section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40eb8-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="40eb8-108">Requirements</span></span>  
 <span data-ttu-id="40eb8-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40eb8-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40eb8-110">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="40eb8-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="40eb8-111">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="40eb8-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="40eb8-112">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40eb8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40eb8-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="40eb8-113">See also</span></span>

- [<span data-ttu-id="40eb8-114">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="40eb8-114">ICeeGen Interface</span></span>](iceegen-interface.md)
