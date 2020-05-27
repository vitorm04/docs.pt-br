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
ms.openlocfilehash: 84791eba7c95d3278bd4650bd7d660e98fcb79d8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008906"
---
# <a name="cvstruct-structure"></a><span data-ttu-id="974bc-102">Estrutura CVStruct</span><span class="sxs-lookup"><span data-stu-id="974bc-102">CVStruct Structure</span></span>
<span data-ttu-id="974bc-103">Contém informações que são usadas ao instalar um módulo ou uma imagem composta.</span><span class="sxs-lookup"><span data-stu-id="974bc-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="974bc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="974bc-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="974bc-105">Membros</span><span class="sxs-lookup"><span data-stu-id="974bc-105">Members</span></span>  
  
|<span data-ttu-id="974bc-106">Membro</span><span class="sxs-lookup"><span data-stu-id="974bc-106">Member</span></span>|<span data-ttu-id="974bc-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="974bc-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="974bc-108">Principal</span><span class="sxs-lookup"><span data-stu-id="974bc-108">Major</span></span>|<span data-ttu-id="974bc-109">Número de Build da versão principal.</span><span class="sxs-lookup"><span data-stu-id="974bc-109">Major version build number.</span></span>|  
|<span data-ttu-id="974bc-110">Secundária</span><span class="sxs-lookup"><span data-stu-id="974bc-110">Minor</span></span>|<span data-ttu-id="974bc-111">Número de Build da versão secundária.</span><span class="sxs-lookup"><span data-stu-id="974bc-111">Minor version build number.</span></span>|  
|<span data-ttu-id="974bc-112">Sub</span><span class="sxs-lookup"><span data-stu-id="974bc-112">Sub</span></span>|<span data-ttu-id="974bc-113">Número de subcompilação.</span><span class="sxs-lookup"><span data-stu-id="974bc-113">Sub-build number.</span></span>|  
|<span data-ttu-id="974bc-114">Build</span><span class="sxs-lookup"><span data-stu-id="974bc-114">Build</span></span>|<span data-ttu-id="974bc-115">Número da compilação.</span><span class="sxs-lookup"><span data-stu-id="974bc-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="974bc-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="974bc-116">Requirements</span></span>  
 <span data-ttu-id="974bc-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="974bc-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="974bc-118">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="974bc-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="974bc-119">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="974bc-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="974bc-120">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="974bc-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="974bc-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="974bc-121">See also</span></span>

- [<span data-ttu-id="974bc-122">Estruturas de metadados</span><span class="sxs-lookup"><span data-stu-id="974bc-122">Metadata Structures</span></span>](metadata-structures.md)
