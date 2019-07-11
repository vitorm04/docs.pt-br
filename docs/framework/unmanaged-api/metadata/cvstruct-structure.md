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
ms.openlocfilehash: b3e35cea4601c8e51eb3021dc9f598ddb881afe0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750713"
---
# <a name="cvstruct-structure"></a><span data-ttu-id="b2dd6-102">Estrutura CVStruct</span><span class="sxs-lookup"><span data-stu-id="b2dd6-102">CVStruct Structure</span></span>
<span data-ttu-id="b2dd6-103">Contém informações que são usadas ao instalar um módulo ou uma imagem composta.</span><span class="sxs-lookup"><span data-stu-id="b2dd6-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2dd6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b2dd6-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="b2dd6-105">Membros</span><span class="sxs-lookup"><span data-stu-id="b2dd6-105">Members</span></span>  
  
|<span data-ttu-id="b2dd6-106">Membro</span><span class="sxs-lookup"><span data-stu-id="b2dd6-106">Member</span></span>|<span data-ttu-id="b2dd6-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b2dd6-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b2dd6-108">Principal</span><span class="sxs-lookup"><span data-stu-id="b2dd6-108">Major</span></span>|<span data-ttu-id="b2dd6-109">Número de build de versão principal.</span><span class="sxs-lookup"><span data-stu-id="b2dd6-109">Major version build number.</span></span>|  
|<span data-ttu-id="b2dd6-110">Secundário</span><span class="sxs-lookup"><span data-stu-id="b2dd6-110">Minor</span></span>|<span data-ttu-id="b2dd6-111">Número de build de versão secundária.</span><span class="sxs-lookup"><span data-stu-id="b2dd6-111">Minor version build number.</span></span>|  
|<span data-ttu-id="b2dd6-112">Sub</span><span class="sxs-lookup"><span data-stu-id="b2dd6-112">Sub</span></span>|<span data-ttu-id="b2dd6-113">Número de subpropriedades de compilação.</span><span class="sxs-lookup"><span data-stu-id="b2dd6-113">Sub-build number.</span></span>|  
|<span data-ttu-id="b2dd6-114">Build</span><span class="sxs-lookup"><span data-stu-id="b2dd6-114">Build</span></span>|<span data-ttu-id="b2dd6-115">número de compilação.</span><span class="sxs-lookup"><span data-stu-id="b2dd6-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b2dd6-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b2dd6-116">Requirements</span></span>  
 <span data-ttu-id="b2dd6-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2dd6-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2dd6-118">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b2dd6-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b2dd6-119">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="b2dd6-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b2dd6-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2dd6-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2dd6-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2dd6-121">See also</span></span>

- [<span data-ttu-id="b2dd6-122">Estruturas de metadados</span><span class="sxs-lookup"><span data-stu-id="b2dd6-122">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
