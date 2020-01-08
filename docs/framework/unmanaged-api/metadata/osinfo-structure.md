---
title: Estrutura OSINFO
ms.date: 03/30/2017
api_name:
- OSINFO
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- OSINFO
helpviewer_keywords:
- OSINFO structure [.NET Framework metadata]
ms.assetid: fac7b480-7adb-4450-a5e9-690fed81ffae
topic_type:
- apiref
ms.openlocfilehash: d66e9bc3a027610d917e15dc9769b92ea1c5fb71
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345596"
---
# <a name="osinfo-structure"></a><span data-ttu-id="11593-102">Estrutura OSINFO</span><span class="sxs-lookup"><span data-stu-id="11593-102">OSINFO Structure</span></span>
<span data-ttu-id="11593-103">Contém detalhes sobre o sistema operacional de um assembly ou módulo.</span><span class="sxs-lookup"><span data-stu-id="11593-103">Contains details about the operating system for an assembly or module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11593-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="11593-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;   
    DWORD   dwOSMinorVersion;   
} OSINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="11593-105">Membros</span><span class="sxs-lookup"><span data-stu-id="11593-105">Members</span></span>  
  
|<span data-ttu-id="11593-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="11593-106">Member</span></span>|<span data-ttu-id="11593-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="11593-107">Description</span></span>|  
|------------|-----------------|  
|`dwOSPlatformId`|<span data-ttu-id="11593-108">Um dos valores de identificador definidos pela função da plataforma Microsoft Windows `GetVersionEx`.</span><span class="sxs-lookup"><span data-stu-id="11593-108">One of the identifier values defined by the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="11593-109">Os valores a seguir têm suporte:</span><span class="sxs-lookup"><span data-stu-id="11593-109">The following values are supported:</span></span><br /><br /> <span data-ttu-id="11593-110">-VER_PLATFORM_WIN32s, ou 0x0000, para especificar o Microsoft Windows 3,1.</span><span class="sxs-lookup"><span data-stu-id="11593-110">-   VER_PLATFORM_WIN32s, or 0x0000, to specify Microsoft Windows 3.1.</span></span><br /><span data-ttu-id="11593-111">-VER_PLATFORM_WIN32_WINDOWS, ou 0x0001, para especificar o Windows 95, o Windows 98 ou os sistemas operacionais decrescentes deles.</span><span class="sxs-lookup"><span data-stu-id="11593-111">-   VER_PLATFORM_WIN32_WINDOWS, or 0x0001, to specify Windows 95, Windows 98, or operating systems descended from them.</span></span><br /><span data-ttu-id="11593-112">-VER_PLATFORM_WIN32_NT, ou 0x0002, para especificar o Windows NT ou os sistemas operacionais que descendem dele.</span><span class="sxs-lookup"><span data-stu-id="11593-112">-   VER_PLATFORM_WIN32_NT, or 0x0002, to specify Windows NT or operating systems descended from it.</span></span>|  
|`dwOSMajorVersion`|<span data-ttu-id="11593-113">A versão principal do sistema operacional ou um valor nulo para indicar qualquer versão.</span><span class="sxs-lookup"><span data-stu-id="11593-113">The operating system major version, or a NULL value to indicate any version.</span></span>|  
|`dwOSMinorVersion`|<span data-ttu-id="11593-114">A versão secundária do sistema operacional ou um valor nulo para indicar qualquer versão.</span><span class="sxs-lookup"><span data-stu-id="11593-114">The operating system minor version, or a NULL value to indicate any version.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11593-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="11593-115">Remarks</span></span>  
 <span data-ttu-id="11593-116">o `OSINFO` é baseado na estrutura de `OSVERSIONINFOEX` que é usada em chamadas para a função da plataforma Microsoft Windows `GetVersionEx`.</span><span class="sxs-lookup"><span data-stu-id="11593-116">`OSINFO` is based on the `OSVERSIONINFOEX` structure that is used in calls to the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="11593-117">Essa estrutura é usada pela estrutura ASSEMBLYMETADATA para indicar o suporte do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="11593-117">This structure is used by the ASSEMBLYMETADATA structure to indicate its operating system support.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11593-118">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="11593-118">Requirements</span></span>  
 <span data-ttu-id="11593-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11593-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11593-120">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="11593-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="11593-121">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="11593-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="11593-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11593-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11593-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="11593-123">See also</span></span>

- [<span data-ttu-id="11593-124">Estruturas de metadados</span><span class="sxs-lookup"><span data-stu-id="11593-124">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="11593-125">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="11593-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
