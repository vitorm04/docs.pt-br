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
ms.openlocfilehash: 048fe687e4d979576896f5310bddc855b40bb695
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175220"
---
# <a name="osinfo-structure"></a><span data-ttu-id="cce02-102">Estrutura OSINFO</span><span class="sxs-lookup"><span data-stu-id="cce02-102">OSINFO Structure</span></span>
<span data-ttu-id="cce02-103">Contém detalhes sobre o sistema operacional para um conjunto ou módulo.</span><span class="sxs-lookup"><span data-stu-id="cce02-103">Contains details about the operating system for an assembly or module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cce02-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cce02-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;
    DWORD   dwOSMinorVersion;
} OSINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="cce02-105">Membros</span><span class="sxs-lookup"><span data-stu-id="cce02-105">Members</span></span>  
  
|<span data-ttu-id="cce02-106">Membro</span><span class="sxs-lookup"><span data-stu-id="cce02-106">Member</span></span>|<span data-ttu-id="cce02-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="cce02-107">Description</span></span>|  
|------------|-----------------|  
|`dwOSPlatformId`|<span data-ttu-id="cce02-108">Um dos valores identificadores definidos `GetVersionEx`pela função da plataforma Microsoft Windows .</span><span class="sxs-lookup"><span data-stu-id="cce02-108">One of the identifier values defined by the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="cce02-109">Os valores a seguir têm suporte:</span><span class="sxs-lookup"><span data-stu-id="cce02-109">The following values are supported:</span></span><br /><br /> <span data-ttu-id="cce02-110">- VER_PLATFORM_WIN32s, ou 0x0000, para especificar o Microsoft Windows 3.1.</span><span class="sxs-lookup"><span data-stu-id="cce02-110">-   VER_PLATFORM_WIN32s, or 0x0000, to specify Microsoft Windows 3.1.</span></span><br /><span data-ttu-id="cce02-111">- VER_PLATFORM_WIN32_WINDOWS, ou 0x0001, para especificar o Windows 95, Windows 98 ou sistemas operacionais descendentes deles.</span><span class="sxs-lookup"><span data-stu-id="cce02-111">-   VER_PLATFORM_WIN32_WINDOWS, or 0x0001, to specify Windows 95, Windows 98, or operating systems descended from them.</span></span><br /><span data-ttu-id="cce02-112">- VER_PLATFORM_WIN32_NT, ou 0x0002, para especificar o Windows NT ou sistemas operacionais descendentes dele.</span><span class="sxs-lookup"><span data-stu-id="cce02-112">-   VER_PLATFORM_WIN32_NT, or 0x0002, to specify Windows NT or operating systems descended from it.</span></span>|  
|`dwOSMajorVersion`|<span data-ttu-id="cce02-113">A versão principal do sistema operacional ou um valor NULL para indicar qualquer versão.</span><span class="sxs-lookup"><span data-stu-id="cce02-113">The operating system major version, or a NULL value to indicate any version.</span></span>|  
|`dwOSMinorVersion`|<span data-ttu-id="cce02-114">A versão menor do sistema operacional ou um valor NULL para indicar qualquer versão.</span><span class="sxs-lookup"><span data-stu-id="cce02-114">The operating system minor version, or a NULL value to indicate any version.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cce02-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="cce02-115">Remarks</span></span>  
 <span data-ttu-id="cce02-116">`OSINFO`baseia-se `OSVERSIONINFOEX` na estrutura usada em chamadas para `GetVersionEx`a função da plataforma Microsoft Windows .</span><span class="sxs-lookup"><span data-stu-id="cce02-116">`OSINFO` is based on the `OSVERSIONINFOEX` structure that is used in calls to the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="cce02-117">Esta estrutura é usada pela estrutura ASSEMBLYMETADATA para indicar o suporte ao sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="cce02-117">This structure is used by the ASSEMBLYMETADATA structure to indicate its operating system support.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cce02-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cce02-118">Requirements</span></span>  
 <span data-ttu-id="cce02-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cce02-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cce02-120">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cce02-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cce02-121">**Biblioteca:** Usado como recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cce02-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cce02-122">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cce02-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cce02-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="cce02-123">See also</span></span>

- [<span data-ttu-id="cce02-124">Estruturas de metadados</span><span class="sxs-lookup"><span data-stu-id="cce02-124">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="cce02-125">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="cce02-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
