---
title: Estrutura CVStruct
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CVStruct
api_location: mscoree.dll
api_type: COM
f1_keywords: CVStruct
helpviewer_keywords: CVStruct structure [.NET Framework metadata]
ms.assetid: e9e4e497-d5fb-464b-991c-3bdd824664fd
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 95c1aeb0cacef929e99e5121f29e2f69b320caec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="cvstruct-structure"></a><span data-ttu-id="8883b-102">Estrutura CVStruct</span><span class="sxs-lookup"><span data-stu-id="8883b-102">CVStruct Structure</span></span>
<span data-ttu-id="8883b-103">Contém informações que são usadas durante a instalação de um módulo ou uma imagem composta.</span><span class="sxs-lookup"><span data-stu-id="8883b-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8883b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8883b-104">Syntax</span></span>  
  
```  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="8883b-105">Membros</span><span class="sxs-lookup"><span data-stu-id="8883b-105">Members</span></span>  
  
|<span data-ttu-id="8883b-106">Membro</span><span class="sxs-lookup"><span data-stu-id="8883b-106">Member</span></span>|<span data-ttu-id="8883b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="8883b-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="8883b-108">Principal</span><span class="sxs-lookup"><span data-stu-id="8883b-108">Major</span></span>|<span data-ttu-id="8883b-109">Número de compilação de versão principal.</span><span class="sxs-lookup"><span data-stu-id="8883b-109">Major version build number.</span></span>|  
|<span data-ttu-id="8883b-110">Secundário</span><span class="sxs-lookup"><span data-stu-id="8883b-110">Minor</span></span>|<span data-ttu-id="8883b-111">Número de compilação de versão secundária.</span><span class="sxs-lookup"><span data-stu-id="8883b-111">Minor version build number.</span></span>|  
|<span data-ttu-id="8883b-112">Sub</span><span class="sxs-lookup"><span data-stu-id="8883b-112">Sub</span></span>|<span data-ttu-id="8883b-113">Número de compilação abaixo.</span><span class="sxs-lookup"><span data-stu-id="8883b-113">Sub-build number.</span></span>|  
|<span data-ttu-id="8883b-114">Build</span><span class="sxs-lookup"><span data-stu-id="8883b-114">Build</span></span>|<span data-ttu-id="8883b-115">Número de compilação.</span><span class="sxs-lookup"><span data-stu-id="8883b-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8883b-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8883b-116">Requirements</span></span>  
 <span data-ttu-id="8883b-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8883b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8883b-118">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8883b-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8883b-119">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="8883b-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8883b-120">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8883b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8883b-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8883b-121">See Also</span></span>  
 [<span data-ttu-id="8883b-122">Estruturas de metadados</span><span class="sxs-lookup"><span data-stu-id="8883b-122">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
