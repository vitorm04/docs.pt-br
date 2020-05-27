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
ms.openlocfilehash: 14942680a79c4d1fcc69092a4f752738db1fb0b0
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008905"
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="3739d-102">Enumeração COUNINITIEE</span><span class="sxs-lookup"><span data-stu-id="3739d-102">COUNINITIEE Enumeration</span></span>
<span data-ttu-id="3739d-103">Especifica constantes usadas por [CoUninitializeEE](../hosting/couninitializeee-function.md) ao inicializar o Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="3739d-103">Specifies constants used by [CoUninitializeEE](../hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3739d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3739d-104">Syntax</span></span>  
  
```cpp  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="3739d-105">Membros</span><span class="sxs-lookup"><span data-stu-id="3739d-105">Members</span></span>  
  
|<span data-ttu-id="3739d-106">Membro</span><span class="sxs-lookup"><span data-stu-id="3739d-106">Member</span></span>|<span data-ttu-id="3739d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="3739d-107">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="3739d-108">Indica o modo de não inicialização padrão.</span><span class="sxs-lookup"><span data-stu-id="3739d-108">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="3739d-109">Indica o modo de não inicialização para descarregar um assembly.</span><span class="sxs-lookup"><span data-stu-id="3739d-109">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3739d-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3739d-110">Requirements</span></span>  
 <span data-ttu-id="3739d-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3739d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3739d-112">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3739d-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3739d-113">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3739d-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3739d-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3739d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3739d-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="3739d-115">See also</span></span>

- [<span data-ttu-id="3739d-116">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="3739d-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
