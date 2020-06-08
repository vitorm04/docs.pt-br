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
ms.openlocfilehash: ab9d7eb6f5760b43fe805443bbe1ea4a95c72069
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501060"
---
# <a name="osinfo-structure"></a><span data-ttu-id="9adee-102">Estrutura OSINFO</span><span class="sxs-lookup"><span data-stu-id="9adee-102">OSINFO Structure</span></span>
<span data-ttu-id="9adee-103">Contém detalhes sobre o sistema operacional de um assembly ou módulo.</span><span class="sxs-lookup"><span data-stu-id="9adee-103">Contains details about the operating system for an assembly or module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9adee-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9adee-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;
    DWORD   dwOSMinorVersion;
} OSINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="9adee-105">Membros</span><span class="sxs-lookup"><span data-stu-id="9adee-105">Members</span></span>  
  
|<span data-ttu-id="9adee-106">Membro</span><span class="sxs-lookup"><span data-stu-id="9adee-106">Member</span></span>|<span data-ttu-id="9adee-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9adee-107">Description</span></span>|  
|------------|-----------------|  
|`dwOSPlatformId`|<span data-ttu-id="9adee-108">Um dos valores de identificador definidos pela função da plataforma Microsoft Windows `GetVersionEx` .</span><span class="sxs-lookup"><span data-stu-id="9adee-108">One of the identifier values defined by the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="9adee-109">Os seguintes valores têm suporte:</span><span class="sxs-lookup"><span data-stu-id="9adee-109">The following values are supported:</span></span><br /><br /> <span data-ttu-id="9adee-110">-VER_PLATFORM_WIN32s, ou 0x0000, para especificar o Microsoft Windows 3,1.</span><span class="sxs-lookup"><span data-stu-id="9adee-110">-   VER_PLATFORM_WIN32s, or 0x0000, to specify Microsoft Windows 3.1.</span></span><br /><span data-ttu-id="9adee-111">-VER_PLATFORM_WIN32_WINDOWS, ou 0x0001, para especificar o Windows 95, o Windows 98 ou os sistemas operacionais decrescentes deles.</span><span class="sxs-lookup"><span data-stu-id="9adee-111">-   VER_PLATFORM_WIN32_WINDOWS, or 0x0001, to specify Windows 95, Windows 98, or operating systems descended from them.</span></span><br /><span data-ttu-id="9adee-112">-VER_PLATFORM_WIN32_NT, ou 0x0002, para especificar o Windows NT ou os sistemas operacionais que descendem dele.</span><span class="sxs-lookup"><span data-stu-id="9adee-112">-   VER_PLATFORM_WIN32_NT, or 0x0002, to specify Windows NT or operating systems descended from it.</span></span>|  
|`dwOSMajorVersion`|<span data-ttu-id="9adee-113">A versão principal do sistema operacional ou um valor nulo para indicar qualquer versão.</span><span class="sxs-lookup"><span data-stu-id="9adee-113">The operating system major version, or a NULL value to indicate any version.</span></span>|  
|`dwOSMinorVersion`|<span data-ttu-id="9adee-114">A versão secundária do sistema operacional ou um valor nulo para indicar qualquer versão.</span><span class="sxs-lookup"><span data-stu-id="9adee-114">The operating system minor version, or a NULL value to indicate any version.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9adee-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="9adee-115">Remarks</span></span>  
 <span data-ttu-id="9adee-116">`OSINFO`baseia-se na `OSVERSIONINFOEX` estrutura usada em chamadas para a função da plataforma Microsoft Windows `GetVersionEx` .</span><span class="sxs-lookup"><span data-stu-id="9adee-116">`OSINFO` is based on the `OSVERSIONINFOEX` structure that is used in calls to the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="9adee-117">Essa estrutura é usada pela estrutura ASSEMBLYMETADATA para indicar o suporte do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="9adee-117">This structure is used by the ASSEMBLYMETADATA structure to indicate its operating system support.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9adee-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9adee-118">Requirements</span></span>  
 <span data-ttu-id="9adee-119">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9adee-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9adee-120">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9adee-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9adee-121">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9adee-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9adee-122">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9adee-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9adee-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="9adee-123">See also</span></span>

- [<span data-ttu-id="9adee-124">Estruturas de metadados</span><span class="sxs-lookup"><span data-stu-id="9adee-124">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="9adee-125">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="9adee-125">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
