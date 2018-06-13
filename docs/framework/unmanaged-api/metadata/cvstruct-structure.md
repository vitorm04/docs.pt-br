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
ms.openlocfilehash: 195f311d58f2169d715bb33986ee6e591622f377
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445037"
---
# <a name="cvstruct-structure"></a><span data-ttu-id="3ec76-102">Estrutura CVStruct</span><span class="sxs-lookup"><span data-stu-id="3ec76-102">CVStruct Structure</span></span>
<span data-ttu-id="3ec76-103">Contém informações que são usadas durante a instalação de um módulo ou uma imagem composta.</span><span class="sxs-lookup"><span data-stu-id="3ec76-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ec76-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3ec76-104">Syntax</span></span>  
  
```  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="3ec76-105">Membros</span><span class="sxs-lookup"><span data-stu-id="3ec76-105">Members</span></span>  
  
|<span data-ttu-id="3ec76-106">Membro</span><span class="sxs-lookup"><span data-stu-id="3ec76-106">Member</span></span>|<span data-ttu-id="3ec76-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="3ec76-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="3ec76-108">Principal</span><span class="sxs-lookup"><span data-stu-id="3ec76-108">Major</span></span>|<span data-ttu-id="3ec76-109">Número de compilação de versão principal.</span><span class="sxs-lookup"><span data-stu-id="3ec76-109">Major version build number.</span></span>|  
|<span data-ttu-id="3ec76-110">Secundário</span><span class="sxs-lookup"><span data-stu-id="3ec76-110">Minor</span></span>|<span data-ttu-id="3ec76-111">Número de compilação de versão secundária.</span><span class="sxs-lookup"><span data-stu-id="3ec76-111">Minor version build number.</span></span>|  
|<span data-ttu-id="3ec76-112">Sub</span><span class="sxs-lookup"><span data-stu-id="3ec76-112">Sub</span></span>|<span data-ttu-id="3ec76-113">Número de compilação abaixo.</span><span class="sxs-lookup"><span data-stu-id="3ec76-113">Sub-build number.</span></span>|  
|<span data-ttu-id="3ec76-114">Build</span><span class="sxs-lookup"><span data-stu-id="3ec76-114">Build</span></span>|<span data-ttu-id="3ec76-115">Número de compilação.</span><span class="sxs-lookup"><span data-stu-id="3ec76-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3ec76-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3ec76-116">Requirements</span></span>  
 <span data-ttu-id="3ec76-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ec76-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ec76-118">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3ec76-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3ec76-119">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="3ec76-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3ec76-120">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ec76-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ec76-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ec76-121">See Also</span></span>  
 [<span data-ttu-id="3ec76-122">Estruturas de metadados</span><span class="sxs-lookup"><span data-stu-id="3ec76-122">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
