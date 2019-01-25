---
title: Método ICeeGen::GetSectionCreate
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionCreate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionCreate
helpviewer_keywords:
- ICeeGen::GetSectionCreate method [.NET Framework metadata]
- GetSectionCreate method [.NET Framework metadata]
ms.assetid: 154b2460-59ce-4874-a9f2-1b3353486ac5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 93e96e7804a3b5ecc64e9e50ce700435be83b77a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643358"
---
# <a name="iceegengetsectioncreate-method"></a><span data-ttu-id="b2df8-102">Método ICeeGen::GetSectionCreate</span><span class="sxs-lookup"><span data-stu-id="b2df8-102">ICeeGen::GetSectionCreate Method</span></span>
<span data-ttu-id="b2df8-103">Gera e obtém uma seção de código usando o nome especificado e os valores de sinalizador.</span><span class="sxs-lookup"><span data-stu-id="b2df8-103">Generates and gets a code section using the specified name and flag values.</span></span>  
  
 <span data-ttu-id="b2df8-104">Esse método é obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="b2df8-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2df8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b2df8-105">Syntax</span></span>  
  
```  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b2df8-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b2df8-106">Parameters</span></span>  
 `name`  
 <span data-ttu-id="b2df8-107">[in] Um ponteiro para uma cadeia de caracteres que especifica o nome da seção a ser criado.</span><span class="sxs-lookup"><span data-stu-id="b2df8-107">[in] A pointer to a string that specifies the name of the section to be created.</span></span>  
  
 `flags`  
 <span data-ttu-id="b2df8-108">[in] Sinalizadores que especificam as opções.</span><span class="sxs-lookup"><span data-stu-id="b2df8-108">[in] Flags that specify options.</span></span>  
  
 `section`  
 <span data-ttu-id="b2df8-109">[out] Um ponteiro para a seção de código recém-criado.</span><span class="sxs-lookup"><span data-stu-id="b2df8-109">[out] A pointer to the newly created code section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2df8-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="b2df8-110">Remarks</span></span>  
 <span data-ttu-id="b2df8-111">Chamar `GetSectionCreate` somente se você tiver requisitos especiais de seção que não são manipulados por outros métodos.</span><span class="sxs-lookup"><span data-stu-id="b2df8-111">Call `GetSectionCreate` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2df8-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b2df8-112">Requirements</span></span>  
 <span data-ttu-id="b2df8-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2df8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2df8-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b2df8-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b2df8-115">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="b2df8-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b2df8-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2df8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2df8-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2df8-117">See also</span></span>
- [<span data-ttu-id="b2df8-118">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="b2df8-118">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
