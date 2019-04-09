---
title: Estrutura CVStruct
ms.date: 03/30/2017
api_name:
- CVStruct
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CVStruct
helpviewer_keywords:
- CVStruct structure [.NET Framework metadata]
ms.assetid: e9e4e497-d5fb-464b-991c-3bdd824664fd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4a5f06b3f79fed5dac5a6f07650e4fabd0aa5867
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142162"
---
# <a name="cvstruct-structure"></a><span data-ttu-id="3d59f-102">Estrutura CVStruct</span><span class="sxs-lookup"><span data-stu-id="3d59f-102">CVStruct Structure</span></span>
<span data-ttu-id="3d59f-103">Contém informações que são usadas ao instalar um módulo ou uma imagem composta.</span><span class="sxs-lookup"><span data-stu-id="3d59f-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d59f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3d59f-104">Syntax</span></span>  
  
```  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="3d59f-105">Membros</span><span class="sxs-lookup"><span data-stu-id="3d59f-105">Members</span></span>  
  
|<span data-ttu-id="3d59f-106">Membro</span><span class="sxs-lookup"><span data-stu-id="3d59f-106">Member</span></span>|<span data-ttu-id="3d59f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="3d59f-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="3d59f-108">Principal</span><span class="sxs-lookup"><span data-stu-id="3d59f-108">Major</span></span>|<span data-ttu-id="3d59f-109">Número de build de versão principal.</span><span class="sxs-lookup"><span data-stu-id="3d59f-109">Major version build number.</span></span>|  
|<span data-ttu-id="3d59f-110">Secundário</span><span class="sxs-lookup"><span data-stu-id="3d59f-110">Minor</span></span>|<span data-ttu-id="3d59f-111">Número de build de versão secundária.</span><span class="sxs-lookup"><span data-stu-id="3d59f-111">Minor version build number.</span></span>|  
|<span data-ttu-id="3d59f-112">Sub</span><span class="sxs-lookup"><span data-stu-id="3d59f-112">Sub</span></span>|<span data-ttu-id="3d59f-113">Número de subpropriedades de compilação.</span><span class="sxs-lookup"><span data-stu-id="3d59f-113">Sub-build number.</span></span>|  
|<span data-ttu-id="3d59f-114">Build</span><span class="sxs-lookup"><span data-stu-id="3d59f-114">Build</span></span>|<span data-ttu-id="3d59f-115">número de compilação.</span><span class="sxs-lookup"><span data-stu-id="3d59f-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3d59f-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3d59f-116">Requirements</span></span>  
 <span data-ttu-id="3d59f-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d59f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d59f-118">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3d59f-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3d59f-119">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="3d59f-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="3d59f-120">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="3d59f-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3d59f-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3d59f-121">See also</span></span>

- [<span data-ttu-id="3d59f-122">Estruturas de metadados</span><span class="sxs-lookup"><span data-stu-id="3d59f-122">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
