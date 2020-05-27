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
ms.openlocfilehash: 0cf7b15392c90694db659f6faff6feecbef65466
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008312"
---
# <a name="iceegengetsectioncreate-method"></a><span data-ttu-id="69950-102">Método ICeeGen::GetSectionCreate</span><span class="sxs-lookup"><span data-stu-id="69950-102">ICeeGen::GetSectionCreate Method</span></span>
<span data-ttu-id="69950-103">Gera e obtém uma seção de código usando os valores de nome e sinalizador especificados.</span><span class="sxs-lookup"><span data-stu-id="69950-103">Generates and gets a code section using the specified name and flag values.</span></span>  
  
 <span data-ttu-id="69950-104">Este método é obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="69950-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69950-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="69950-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69950-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="69950-106">Parameters</span></span>  
 `name`  
 <span data-ttu-id="69950-107">no Um ponteiro para uma cadeia de caracteres que especifica o nome da seção a ser criada.</span><span class="sxs-lookup"><span data-stu-id="69950-107">[in] A pointer to a string that specifies the name of the section to be created.</span></span>  
  
 `flags`  
 <span data-ttu-id="69950-108">no Sinalizadores que especificam opções.</span><span class="sxs-lookup"><span data-stu-id="69950-108">[in] Flags that specify options.</span></span>  
  
 `section`  
 <span data-ttu-id="69950-109">fora Um ponteiro para a seção de código recém-criada.</span><span class="sxs-lookup"><span data-stu-id="69950-109">[out] A pointer to the newly created code section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69950-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="69950-110">Remarks</span></span>  
 <span data-ttu-id="69950-111">Chame `GetSectionCreate` somente se você tiver requisitos de seção especiais que não são tratados por outros métodos.</span><span class="sxs-lookup"><span data-stu-id="69950-111">Call `GetSectionCreate` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69950-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="69950-112">Requirements</span></span>  
 <span data-ttu-id="69950-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69950-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69950-114">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="69950-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="69950-115">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="69950-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="69950-116">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69950-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69950-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="69950-117">See also</span></span>

- [<span data-ttu-id="69950-118">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="69950-118">ICeeGen Interface</span></span>](iceegen-interface.md)
