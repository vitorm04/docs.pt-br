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
ms.openlocfilehash: 57054bdb7e3b991bc81985c02ec72a4110f31d60
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436442"
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="f1b3a-102">Enumeração COUNINITIEE</span><span class="sxs-lookup"><span data-stu-id="f1b3a-102">COUNINITIEE Enumeration</span></span>
<span data-ttu-id="f1b3a-103">Especifica constantes usadas por [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) ao inicializar o Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="f1b3a-103">Specifies constants used by [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1b3a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f1b3a-104">Syntax</span></span>  
  
```cpp  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,   
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="f1b3a-105">Membros</span><span class="sxs-lookup"><span data-stu-id="f1b3a-105">Members</span></span>  
  
|<span data-ttu-id="f1b3a-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="f1b3a-106">Member</span></span>|<span data-ttu-id="f1b3a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1b3a-107">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="f1b3a-108">Indica o modo de não inicialização padrão.</span><span class="sxs-lookup"><span data-stu-id="f1b3a-108">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="f1b3a-109">Indica o modo de não inicialização para descarregar um assembly.</span><span class="sxs-lookup"><span data-stu-id="f1b3a-109">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f1b3a-110">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="f1b3a-110">Requirements</span></span>  
 <span data-ttu-id="f1b3a-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1b3a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1b3a-112">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f1b3a-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f1b3a-113">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f1b3a-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f1b3a-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1b3a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1b3a-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1b3a-115">See also</span></span>

- [<span data-ttu-id="f1b3a-116">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="f1b3a-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
