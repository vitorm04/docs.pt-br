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
ms.openlocfilehash: bae19ec18c54eccc7aa54d2d3a006f36ba8ab762
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110871"
---
# <a name="assemblyinfo-structure"></a><span data-ttu-id="d1fed-102">Estrutura ASSEMBLY_INFO</span><span class="sxs-lookup"><span data-stu-id="d1fed-102">ASSEMBLY_INFO Structure</span></span>
<span data-ttu-id="d1fed-103">Contém informações sobre um assembly que está registrado no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="d1fed-103">Contains information about an assembly that is registered in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1fed-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d1fed-104">Syntax</span></span>  
  
```  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="d1fed-105">Membros</span><span class="sxs-lookup"><span data-stu-id="d1fed-105">Members</span></span>  
  
|<span data-ttu-id="d1fed-106">Membro</span><span class="sxs-lookup"><span data-stu-id="d1fed-106">Member</span></span>|<span data-ttu-id="d1fed-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d1fed-107">Description</span></span>|  
|------------|-----------------|  
|`cbAssemblyInfo`|<span data-ttu-id="d1fed-108">O tamanho, em bytes, da estrutura.</span><span class="sxs-lookup"><span data-stu-id="d1fed-108">The size, in bytes, of the structure.</span></span> <span data-ttu-id="d1fed-109">Este campo é reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="d1fed-109">This field is reserved for future extensibility.</span></span>|  
|`dwAssemblyFlags`|<span data-ttu-id="d1fed-110">Sinalizadores que indicam os detalhes da instalação sobre o assembly.</span><span class="sxs-lookup"><span data-stu-id="d1fed-110">Flags that indicate installation details about the assembly.</span></span> <span data-ttu-id="d1fed-111">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="d1fed-111">The following values are supported:</span></span><br /><br /> <span data-ttu-id="d1fed-112">-O valor ASSEMBLYINFO_FLAG_INSTALLED, que indica que o assembly está instalado.</span><span class="sxs-lookup"><span data-stu-id="d1fed-112">-   The ASSEMBLYINFO_FLAG_INSTALLED value, which indicates that the assembly is installed.</span></span> <span data-ttu-id="d1fed-113">A versão atual do .NET Framework sempre define `dwAssemblyFlags` para esse valor.</span><span class="sxs-lookup"><span data-stu-id="d1fed-113">The current version of the .NET Framework always sets `dwAssemblyFlags` to this value.</span></span><br /><span data-ttu-id="d1fed-114">-O valor ASSEMBLYINFO_FLAG_PAYLOADRESIDENT, que indica que o assembly é uma carga residente.</span><span class="sxs-lookup"><span data-stu-id="d1fed-114">-   The ASSEMBLYINFO_FLAG_PAYLOADRESIDENT value, which indicates that the assembly is a payload resident.</span></span> <span data-ttu-id="d1fed-115">A versão atual do .NET Framework define nunca `dwAssemblyFlags` para esse valor.</span><span class="sxs-lookup"><span data-stu-id="d1fed-115">The current version of the .NET Framework never sets `dwAssemblyFlags` to this value.</span></span>|  
|`uliAssemblySizeInKB`|<span data-ttu-id="d1fed-116">O tamanho total, em quilobytes, de arquivos que contém o assembly.</span><span class="sxs-lookup"><span data-stu-id="d1fed-116">The total size, in kilobytes, of the files that the assembly contains.</span></span>|  
|`pszCurrentAssemblyPathBuf`|<span data-ttu-id="d1fed-117">Um ponteiro para um buffer de cadeia de caracteres que contém o caminho atual para o arquivo de manifesto.</span><span class="sxs-lookup"><span data-stu-id="d1fed-117">A pointer to a string buffer that holds the current path to the manifest file.</span></span> <span data-ttu-id="d1fed-118">O caminho deve terminar com um caractere nulo.</span><span class="sxs-lookup"><span data-stu-id="d1fed-118">The path must end with a null character.</span></span>|  
|`cchBuf`|<span data-ttu-id="d1fed-119">O número de caracteres largos, incluindo o terminador nulo, que `pszCurrentAssemblyPathBuf` contém.</span><span class="sxs-lookup"><span data-stu-id="d1fed-119">The number of wide characters, including the null terminator, that `pszCurrentAssemblyPathBuf` contains.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d1fed-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d1fed-120">Requirements</span></span>  
 <span data-ttu-id="d1fed-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1fed-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1fed-122">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="d1fed-122">**Header:** Fusion.h</span></span>  
  
 **<span data-ttu-id="d1fed-123">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="d1fed-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d1fed-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d1fed-124">See also</span></span>

- [<span data-ttu-id="d1fed-125">Estruturas de fusão</span><span class="sxs-lookup"><span data-stu-id="d1fed-125">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
- [<span data-ttu-id="d1fed-126">Cache de assemblies global</span><span class="sxs-lookup"><span data-stu-id="d1fed-126">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
