---
title: Estrutura ASSEMBLY_INFO
ms.date: 03/30/2017
api_name:
- ASSEMBLY_INFO
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASSEMBLY_INFO
helpviewer_keywords:
- ASSEMBLY_INFO structure [.NET Framework fusion]
ms.assetid: b3cbb47c-457f-4083-8895-49562ca99ab8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 390ab4881396bbc01337d087f05b6066153bfed1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795491"
---
# <a name="assembly_info-structure"></a><span data-ttu-id="d8c14-102">Estrutura ASSEMBLY_INFO</span><span class="sxs-lookup"><span data-stu-id="d8c14-102">ASSEMBLY_INFO Structure</span></span>
<span data-ttu-id="d8c14-103">Contém informações sobre um assembly que é registrado no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="d8c14-103">Contains information about an assembly that is registered in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8c14-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d8c14-104">Syntax</span></span>  
  
```cpp  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="d8c14-105">Membros</span><span class="sxs-lookup"><span data-stu-id="d8c14-105">Members</span></span>  
  
|<span data-ttu-id="d8c14-106">Membro</span><span class="sxs-lookup"><span data-stu-id="d8c14-106">Member</span></span>|<span data-ttu-id="d8c14-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d8c14-107">Description</span></span>|  
|------------|-----------------|  
|`cbAssemblyInfo`|<span data-ttu-id="d8c14-108">O tamanho, em bytes, da estrutura.</span><span class="sxs-lookup"><span data-stu-id="d8c14-108">The size, in bytes, of the structure.</span></span> <span data-ttu-id="d8c14-109">Este campo é reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="d8c14-109">This field is reserved for future extensibility.</span></span>|  
|`dwAssemblyFlags`|<span data-ttu-id="d8c14-110">Sinalizadores que indicam os detalhes da instalação sobre o assembly.</span><span class="sxs-lookup"><span data-stu-id="d8c14-110">Flags that indicate installation details about the assembly.</span></span> <span data-ttu-id="d8c14-111">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="d8c14-111">The following values are supported:</span></span><br /><br /> <span data-ttu-id="d8c14-112">-O valor ASSEMBLYINFO_FLAG_INSTALLED, que indica que o assembly está instalado.</span><span class="sxs-lookup"><span data-stu-id="d8c14-112">-   The ASSEMBLYINFO_FLAG_INSTALLED value, which indicates that the assembly is installed.</span></span> <span data-ttu-id="d8c14-113">A versão atual do .NET Framework sempre é definida `dwAssemblyFlags` para esse valor.</span><span class="sxs-lookup"><span data-stu-id="d8c14-113">The current version of the .NET Framework always sets `dwAssemblyFlags` to this value.</span></span><br /><span data-ttu-id="d8c14-114">-O valor ASSEMBLYINFO_FLAG_PAYLOADRESIDENT, que indica que o assembly é um conteúdo residente.</span><span class="sxs-lookup"><span data-stu-id="d8c14-114">-   The ASSEMBLYINFO_FLAG_PAYLOADRESIDENT value, which indicates that the assembly is a payload resident.</span></span> <span data-ttu-id="d8c14-115">A versão atual do .NET Framework nunca é definida `dwAssemblyFlags` para esse valor.</span><span class="sxs-lookup"><span data-stu-id="d8c14-115">The current version of the .NET Framework never sets `dwAssemblyFlags` to this value.</span></span>|  
|`uliAssemblySizeInKB`|<span data-ttu-id="d8c14-116">O tamanho total, em quilobytes, dos arquivos que o assembly contém.</span><span class="sxs-lookup"><span data-stu-id="d8c14-116">The total size, in kilobytes, of the files that the assembly contains.</span></span>|  
|`pszCurrentAssemblyPathBuf`|<span data-ttu-id="d8c14-117">Um ponteiro para um buffer de cadeia de caracteres que contém o caminho atual para o arquivo de manifesto.</span><span class="sxs-lookup"><span data-stu-id="d8c14-117">A pointer to a string buffer that holds the current path to the manifest file.</span></span> <span data-ttu-id="d8c14-118">O caminho deve terminar com um caractere nulo.</span><span class="sxs-lookup"><span data-stu-id="d8c14-118">The path must end with a null character.</span></span>|  
|`cchBuf`|<span data-ttu-id="d8c14-119">O número de caracteres largos, incluindo o terminador nulo `pszCurrentAssemblyPathBuf` , que contém.</span><span class="sxs-lookup"><span data-stu-id="d8c14-119">The number of wide characters, including the null terminator, that `pszCurrentAssemblyPathBuf` contains.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d8c14-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d8c14-120">Requirements</span></span>  
 <span data-ttu-id="d8c14-121">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8c14-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8c14-122">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="d8c14-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d8c14-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8c14-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8c14-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8c14-124">See also</span></span>

- [<span data-ttu-id="d8c14-125">Estruturas de fusão</span><span class="sxs-lookup"><span data-stu-id="d8c14-125">Fusion Structures</span></span>](fusion-structures.md)
- [<span data-ttu-id="d8c14-126">Cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="d8c14-126">Global Assembly Cache</span></span>](../../app-domains/gac.md)
