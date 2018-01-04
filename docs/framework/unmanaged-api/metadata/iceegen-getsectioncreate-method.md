---
title: "Método ICeeGen::GetSectionCreate"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.GetSectionCreate
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::GetSectionCreate
helpviewer_keywords:
- ICeeGen::GetSectionCreate method [.NET Framework metadata]
- GetSectionCreate method [.NET Framework metadata]
ms.assetid: 154b2460-59ce-4874-a9f2-1b3353486ac5
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a069f65d3059bfa427ea20623ff9a2ac4049fd39
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iceegengetsectioncreate-method"></a><span data-ttu-id="82a4d-102">Método ICeeGen::GetSectionCreate</span><span class="sxs-lookup"><span data-stu-id="82a4d-102">ICeeGen::GetSectionCreate Method</span></span>
<span data-ttu-id="82a4d-103">Gera e obtém uma seção de código usando o nome especificado e os valores de sinalizador.</span><span class="sxs-lookup"><span data-stu-id="82a4d-103">Generates and gets a code section using the specified name and flag values.</span></span>  
  
 <span data-ttu-id="82a4d-104">Esse método está obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="82a4d-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82a4d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="82a4d-105">Syntax</span></span>  
  
```  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="82a4d-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="82a4d-106">Parameters</span></span>  
 `name`  
 <span data-ttu-id="82a4d-107">[in] Um ponteiro para uma cadeia de caracteres que especifica o nome da seção a ser criado.</span><span class="sxs-lookup"><span data-stu-id="82a4d-107">[in] A pointer to a string that specifies the name of the section to be created.</span></span>  
  
 `flags`  
 <span data-ttu-id="82a4d-108">[in] Sinalizadores que especificam as opções.</span><span class="sxs-lookup"><span data-stu-id="82a4d-108">[in] Flags that specify options.</span></span>  
  
 `section`  
 <span data-ttu-id="82a4d-109">[out] Um ponteiro para a seção de código recém-criado.</span><span class="sxs-lookup"><span data-stu-id="82a4d-109">[out] A pointer to the newly created code section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82a4d-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="82a4d-110">Remarks</span></span>  
 <span data-ttu-id="82a4d-111">Chamar `GetSectionCreate` somente se você tiver requisitos especiais de seção que não são manipulados por outros métodos.</span><span class="sxs-lookup"><span data-stu-id="82a4d-111">Call `GetSectionCreate` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82a4d-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="82a4d-112">Requirements</span></span>  
 <span data-ttu-id="82a4d-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82a4d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82a4d-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="82a4d-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="82a4d-115">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="82a4d-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="82a4d-116">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82a4d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82a4d-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82a4d-117">See Also</span></span>  
 [<span data-ttu-id="82a4d-118">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="82a4d-118">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
