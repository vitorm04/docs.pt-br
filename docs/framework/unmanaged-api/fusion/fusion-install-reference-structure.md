---
title: Estrutura FUSION_INSTALL_REFERENCE
ms.date: 03/30/2017
api_name:
- FUSION_INSTALL_REFERENCE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- FUSION_INSTALL_REFERENCE
helpviewer_keywords:
- FUSION_INSTALL_REFERENCE structure [.NET Framework fusion]
ms.assetid: ae181ec8-36bf-4ed1-9a02-ca27d417c80b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 611b4a543a1de7c6163ec45ff7f17d07726569ba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936479"
---
# <a name="fusioninstallreference-structure"></a><span data-ttu-id="e6bcb-102">Estrutura FUSION_INSTALL_REFERENCE</span><span class="sxs-lookup"><span data-stu-id="e6bcb-102">FUSION_INSTALL_REFERENCE Structure</span></span>
<span data-ttu-id="e6bcb-103">Representa uma referência que um aplicativo faz a um assembly que o aplicativo instalado no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="e6bcb-103">Represents a reference that an application makes to an assembly that the application has installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6bcb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e6bcb-104">Syntax</span></span>  
  
```  
typedef struct _FUSION_INSTALL_REFERENCE_ {  
    DWORD    cbSize,  
    DWORD    dwFlags,  
    GUID     guidScheme,  
    LPCWSTR  szIdentifier,  
    LPCWSTR  szNonCanonicalData  
} FUSION_INSTALL_REFERENCE, *LPFUSION_INSTALL_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="e6bcb-105">Membros</span><span class="sxs-lookup"><span data-stu-id="e6bcb-105">Members</span></span>  
  
|<span data-ttu-id="e6bcb-106">Membro</span><span class="sxs-lookup"><span data-stu-id="e6bcb-106">Member</span></span>|<span data-ttu-id="e6bcb-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e6bcb-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="e6bcb-108">O tamanho da estrutura em bytes.</span><span class="sxs-lookup"><span data-stu-id="e6bcb-108">The size of the structure in bytes.</span></span>|  
|`dwFlags`|<span data-ttu-id="e6bcb-109">Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="e6bcb-109">Reserved for future extensibility.</span></span> <span data-ttu-id="e6bcb-110">Esse valor deve ser 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="e6bcb-110">This value must be 0 (zero).</span></span>|  
|`guidScheme`|<span data-ttu-id="e6bcb-111">A entidade que adiciona a referência.</span><span class="sxs-lookup"><span data-stu-id="e6bcb-111">The entity that adds the reference.</span></span> <span data-ttu-id="e6bcb-112">Este campo pode ter um dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="e6bcb-112">This field can have one of the following values:</span></span><br /><br /> <span data-ttu-id="e6bcb-113">-   FUSION_REFCOUNT_MSI_GUID: O assembly é referenciado por um aplicativo que foi instalado usando o Microsoft Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="e6bcb-113">-   FUSION_REFCOUNT_MSI_GUID: The assembly is referenced by an application that was installed using the Microsoft Windows Installer.</span></span> <span data-ttu-id="e6bcb-114">O `szIdentifier` campo é definido como `MSI`e o `szNonCanonicalData` campo é definido como `Windows Installer`.</span><span class="sxs-lookup"><span data-stu-id="e6bcb-114">The `szIdentifier` field is set to `MSI`, and the `szNonCanonicalData` field is set to `Windows Installer`.</span></span> <span data-ttu-id="e6bcb-115">Esse esquema é usado para os assemblies do Windows lado a lado.</span><span class="sxs-lookup"><span data-stu-id="e6bcb-115">This scheme is used for Windows side-by-side assemblies.</span></span><br /><span data-ttu-id="e6bcb-116">-   FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: O assembly é referenciado por um aplicativo que aparece na **adicionar ou remover programas** interface.</span><span class="sxs-lookup"><span data-stu-id="e6bcb-116">-   FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: The assembly is referenced by an application that appears in the **Add/Remove Programs** interface.</span></span> <span data-ttu-id="e6bcb-117">O `szIdentifier` campo fornece o token que registra o aplicativo com o **Adicionar/remover programas** interface.</span><span class="sxs-lookup"><span data-stu-id="e6bcb-117">The `szIdentifier` field provides the token that registers the application with the **Add/Remove Programs** interface.</span></span><br /><span data-ttu-id="e6bcb-118">-   FUSION_REFCOUNT_FILEPATH_GUID: O assembly é referenciado por um aplicativo que é representado por um arquivo no sistema de arquivos.</span><span class="sxs-lookup"><span data-stu-id="e6bcb-118">-   FUSION_REFCOUNT_FILEPATH_GUID: The assembly is referenced by an application that is represented by a file in the file system.</span></span> <span data-ttu-id="e6bcb-119">O `szIdentifier` campo fornece o caminho para esse arquivo.</span><span class="sxs-lookup"><span data-stu-id="e6bcb-119">The `szIdentifier` field provides the path to this file.</span></span><br /><span data-ttu-id="e6bcb-120">-   FUSION_REFCOUNT_OPAQUE_STRING_GUID: O assembly é referenciado por um aplicativo que é representado somente por uma cadeia de caracteres opaca.</span><span class="sxs-lookup"><span data-stu-id="e6bcb-120">-   FUSION_REFCOUNT_OPAQUE_STRING_GUID: The assembly is referenced by an application that is represented only by an opaque string.</span></span> <span data-ttu-id="e6bcb-121">O `szIdentifier` campo fornece essa cadeia de caracteres opaca.</span><span class="sxs-lookup"><span data-stu-id="e6bcb-121">The `szIdentifier` field provides this opaque string.</span></span> <span data-ttu-id="e6bcb-122">O cache de assembly global não verifica a existência de referências opacas quando você remove esse valor.</span><span class="sxs-lookup"><span data-stu-id="e6bcb-122">The global assembly cache does not check for the existence of opaque references when you remove this value.</span></span><br /><span data-ttu-id="e6bcb-123">-   FUSION_REFCOUNT_OSINSTALL_GUID: Esse valor é reservado.</span><span class="sxs-lookup"><span data-stu-id="e6bcb-123">-   FUSION_REFCOUNT_OSINSTALL_GUID: This value is reserved.</span></span>|  
|`szIdentifier`|<span data-ttu-id="e6bcb-124">Uma cadeia de caracteres exclusiva que identifica o aplicativo que instalou o assembly no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="e6bcb-124">A unique string that identifies the application that installed the assembly in the global assembly cache.</span></span> <span data-ttu-id="e6bcb-125">Seu valor depende do valor da `guidScheme` campo.</span><span class="sxs-lookup"><span data-stu-id="e6bcb-125">Its value depends upon the value of the `guidScheme` field.</span></span>|  
|`szNonCanonicalData`|<span data-ttu-id="e6bcb-126">Uma cadeia de caracteres que é entendida apenas pela entidade que adiciona a referência.</span><span class="sxs-lookup"><span data-stu-id="e6bcb-126">A string that is understood only by the entity that adds the reference.</span></span> <span data-ttu-id="e6bcb-127">O cache de assembly global armazena essa cadeia de caracteres, mas não usá-lo.</span><span class="sxs-lookup"><span data-stu-id="e6bcb-127">The global assembly cache stores this string, but does not use it.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e6bcb-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e6bcb-128">Requirements</span></span>  
 <span data-ttu-id="e6bcb-129">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6bcb-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6bcb-130">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="e6bcb-130">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e6bcb-131">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6bcb-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6bcb-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6bcb-132">See also</span></span>

- [<span data-ttu-id="e6bcb-133">Estruturas de fusão</span><span class="sxs-lookup"><span data-stu-id="e6bcb-133">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
- [<span data-ttu-id="e6bcb-134">Cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="e6bcb-134">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
