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
ms.openlocfilehash: 2c3c3a0168216902e5982b7d0193e72acc2bdf47
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448102"
---
# <a name="iceegengetsectioncreate-method"></a><span data-ttu-id="4613a-102">Método ICeeGen::GetSectionCreate</span><span class="sxs-lookup"><span data-stu-id="4613a-102">ICeeGen::GetSectionCreate Method</span></span>
<span data-ttu-id="4613a-103">Gera e obtém uma seção de código usando os valores de nome e sinalizador especificados.</span><span class="sxs-lookup"><span data-stu-id="4613a-103">Generates and gets a code section using the specified name and flag values.</span></span>  
  
 <span data-ttu-id="4613a-104">Este método é obsoleto e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="4613a-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4613a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4613a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4613a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4613a-106">Parameters</span></span>  
 `name`  
 <span data-ttu-id="4613a-107">no Um ponteiro para uma cadeia de caracteres que especifica o nome da seção a ser criada.</span><span class="sxs-lookup"><span data-stu-id="4613a-107">[in] A pointer to a string that specifies the name of the section to be created.</span></span>  
  
 `flags`  
 <span data-ttu-id="4613a-108">no Sinalizadores que especificam opções.</span><span class="sxs-lookup"><span data-stu-id="4613a-108">[in] Flags that specify options.</span></span>  
  
 `section`  
 <span data-ttu-id="4613a-109">fora Um ponteiro para a seção de código recém-criada.</span><span class="sxs-lookup"><span data-stu-id="4613a-109">[out] A pointer to the newly created code section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4613a-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="4613a-110">Remarks</span></span>  
 <span data-ttu-id="4613a-111">Chame `GetSectionCreate` somente se você tiver requisitos de seção especiais que não são tratados por outros métodos.</span><span class="sxs-lookup"><span data-stu-id="4613a-111">Call `GetSectionCreate` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4613a-112">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="4613a-112">Requirements</span></span>  
 <span data-ttu-id="4613a-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4613a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4613a-114">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4613a-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4613a-115">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4613a-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4613a-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4613a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4613a-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4613a-117">See also</span></span>

- [<span data-ttu-id="4613a-118">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="4613a-118">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
