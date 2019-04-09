---
title: Enumeração CorNativeLinkFlags
ms.date: 03/30/2017
api_name:
- CorNativeLinkFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkFlags
helpviewer_keywords:
- CorNativeLinkFlags enumeration [.NET Framework metadata]
ms.assetid: 8027df7c-cfad-4724-bda0-7538d9519070
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7e6eb2a30dd6722309fd80c1611ad9200ab14ae5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151990"
---
# <a name="cornativelinkflags-enumeration"></a><span data-ttu-id="c69a5-102">Enumeração CorNativeLinkFlags</span><span class="sxs-lookup"><span data-stu-id="c69a5-102">CorNativeLinkFlags Enumeration</span></span>
<span data-ttu-id="c69a5-103">Fornece valores de sinalizador usados pelo vinculador ao vincular o código nativo.</span><span class="sxs-lookup"><span data-stu-id="c69a5-103">Provides flag values used by the linker when linking native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c69a5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c69a5-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    nlfNone         = 0x00,  
    nlfLastError    = 0x01,  
    nlfNoMangle     = 0x02,  
    nlfMaxValue     = 0x03  
} CorNativeLinkFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="c69a5-105">Membros</span><span class="sxs-lookup"><span data-stu-id="c69a5-105">Members</span></span>  
  
|<span data-ttu-id="c69a5-106">Membro</span><span class="sxs-lookup"><span data-stu-id="c69a5-106">Member</span></span>|<span data-ttu-id="c69a5-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c69a5-107">Description</span></span>|  
|------------|-----------------|  
|`nlfNone`|<span data-ttu-id="c69a5-108">Não indica que nenhum sinalizador.</span><span class="sxs-lookup"><span data-stu-id="c69a5-108">Indicates no flags.</span></span>|  
|`nlfLastError`|<span data-ttu-id="c69a5-109">Indica um `setLastError` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="c69a5-109">Indicates a `setLastError` keyword.</span></span>|  
|`nlfNoMangle`|<span data-ttu-id="c69a5-110">Indica um `nomangle` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="c69a5-110">Indicates a `nomangle` keyword.</span></span>|  
|`nlfMaxValue`|<span data-ttu-id="c69a5-111">Não usado.</span><span class="sxs-lookup"><span data-stu-id="c69a5-111">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c69a5-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c69a5-112">Requirements</span></span>  
 <span data-ttu-id="c69a5-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c69a5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c69a5-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c69a5-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c69a5-115">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c69a5-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="c69a5-116">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="c69a5-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c69a5-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c69a5-117">See also</span></span>

- [<span data-ttu-id="c69a5-118">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="c69a5-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
