---
title: Enumeração COUNINITIEE
ms.date: 03/30/2017
api_name:
- COUNINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COUNINITIEE
helpviewer_keywords:
- COUNINITIEE enumeration [.NET Framework metadata]
ms.assetid: c42baa79-f469-4330-95a2-baf7f021c2fc
topic_type:
- apiref
ms.openlocfilehash: e5cbd8c5b1bb048088fe137b1359d0bb9e29af20
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176117"
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="c4e98-102">Enumeração COUNINITIEE</span><span class="sxs-lookup"><span data-stu-id="c4e98-102">COUNINITIEE Enumeration</span></span>
<span data-ttu-id="c4e98-103">Especifica as constantes usadas pelo [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) ao inicializar o tempo de execução do idioma comum.</span><span class="sxs-lookup"><span data-stu-id="c4e98-103">Specifies constants used by [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4e98-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c4e98-104">Syntax</span></span>  
  
```cpp  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="c4e98-105">Membros</span><span class="sxs-lookup"><span data-stu-id="c4e98-105">Members</span></span>  
  
|<span data-ttu-id="c4e98-106">Membro</span><span class="sxs-lookup"><span data-stu-id="c4e98-106">Member</span></span>|<span data-ttu-id="c4e98-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c4e98-107">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="c4e98-108">Indica o modo de não inicialização padrão.</span><span class="sxs-lookup"><span data-stu-id="c4e98-108">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="c4e98-109">Indica modo de desinicialização para descarregar um conjunto.</span><span class="sxs-lookup"><span data-stu-id="c4e98-109">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c4e98-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c4e98-110">Requirements</span></span>  
 <span data-ttu-id="c4e98-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4e98-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4e98-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c4e98-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c4e98-113">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c4e98-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c4e98-114">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4e98-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4e98-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="c4e98-115">See also</span></span>

- [<span data-ttu-id="c4e98-116">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="c4e98-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
