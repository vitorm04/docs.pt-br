---
title: Enumeração CorLinkerOptions
ms.date: 03/30/2017
api_name:
- CorLinkerOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorLinkerOptions
helpviewer_keywords:
- CorLinkerOptions enumeration [.NET Framework metadata]
ms.assetid: a656aad6-cc7e-4994-8251-004a6a45e18f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dc0554ed89d21607978d059b26c4ad69e59a2d4c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045781"
---
# <a name="corlinkeroptions-enumeration"></a><span data-ttu-id="2c7e4-102">Enumeração CorLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="2c7e4-102">CorLinkerOptions Enumeration</span></span>
<span data-ttu-id="2c7e4-103">Especifica os sinalizadores para selecionar opções para o vinculador de metadados.</span><span class="sxs-lookup"><span data-stu-id="2c7e4-103">Specifies flags to select options for the metadata linker.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c7e4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2c7e4-104">Syntax</span></span>  
  
```  
typedef enum CorLinkerOptions {  
    MDAssembly          = 0x00000000,  
    MDNetModule         = 0x00000001,  
} CorLinkerOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="2c7e4-105">Membros</span><span class="sxs-lookup"><span data-stu-id="2c7e4-105">Members</span></span>  
  
|<span data-ttu-id="2c7e4-106">Membro</span><span class="sxs-lookup"><span data-stu-id="2c7e4-106">Member</span></span>|<span data-ttu-id="2c7e4-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2c7e4-107">Description</span></span>|  
|------------|-----------------|  
|`MDAssembly`|<span data-ttu-id="2c7e4-108">As funções globais e tipos privados não são preservadas.</span><span class="sxs-lookup"><span data-stu-id="2c7e4-108">The private types and global functions are not preserved.</span></span>|  
|`MDNetModule`|<span data-ttu-id="2c7e4-109">As funções globais e tipos privados são preservadas.</span><span class="sxs-lookup"><span data-stu-id="2c7e4-109">The private types and global functions are preserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2c7e4-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2c7e4-110">Requirements</span></span>  
 <span data-ttu-id="2c7e4-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c7e4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c7e4-112">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="2c7e4-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="2c7e4-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c7e4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c7e4-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2c7e4-114">See also</span></span>

- [<span data-ttu-id="2c7e4-115">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="2c7e4-115">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
