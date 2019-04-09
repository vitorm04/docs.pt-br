---
title: Enumeração ASM_DISPLAY_FLAGS
ms.date: 03/30/2017
api_name:
- ASM_DISPLAY_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASM_DISPLAY_FLAGS
helpviewer_keywords:
- ASM_DISPLAY_FLAGS enumeration [.NET Framework fusion]
ms.assetid: dbade6c9-9d26-4a79-9fd2-46108edd12d7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbcff46b1932f3293fba4fda922e78f3b9ac37b0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148844"
---
# <a name="asmdisplayflags-enumeration"></a><span data-ttu-id="f979e-102">Enumeração ASM_DISPLAY_FLAGS</span><span class="sxs-lookup"><span data-stu-id="f979e-102">ASM_DISPLAY_FLAGS Enumeration</span></span>
<span data-ttu-id="f979e-103">Indica a versão, compilação, cultura, assinatura e assim por diante, do assembly cujo nome de exibição será recuperado pelo [iassemblyname:: GetDisplayName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="f979e-103">Indicates the version, build, culture, signature, and so on, of the assembly whose display name will be retrieved by the [IAssemblyName::GetDisplayName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f979e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f979e-104">Syntax</span></span>  
  
```  
typedef enum {  
  
    ASM_DISPLAYF_VERSION                 = 0x01,  
    ASM_DISPLAYF_CULTURE                 = 0x02,  
    ASM_DISPLAYF_PUBLIC_KEY_TOKEN        = 0x04,  
    ASM_DISPLAYF_PUBLIC_KEY              = 0x08,  
    ASM_DISPLAYF_CUSTOM                  = 0x10,  
    ASM_DISPLAYF_PROCESSORARCHITECTURE   = 0x20,  
    ASM_DISPLAYF_LANGUAGEID              = 0x40,  
    ASM_DISPLAYF_RETARGET                = 0x80,  
    ASM_DISPLAYF_CONFIG_MASK             = 0x100,  
    ASM_DISPLAYF_MVID                    = 0x200,  
    ASM_DISPLAYF_FULL                    =   
                      ASM_DISPLAYF_VERSION           |   
                      ASM_DISPLAYF_CULTURE           |   
                      ASM_DISPLAYF_PUBLIC_KEY_TOKEN  |   
                      ASM_DISPLAYF_RETARGET          |   
                      ASM_DISPLAYF_PROCESSORARCHITECTURE  
  
} ASM_DISPLAY_FLAGS;  
```  
  
## <a name="remarks"></a><span data-ttu-id="f979e-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="f979e-105">Remarks</span></span>  
 `ASM_DISPLAYF_FULL` <span data-ttu-id="f979e-106">reflete todas as alterações feitas para a versão dos [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="f979e-106">reflects any changes made to the version of the [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span> <span data-ttu-id="f979e-107">Não suponha que o valor retornado é imutável.</span><span class="sxs-lookup"><span data-stu-id="f979e-107">Do not assume that the returned value is immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f979e-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f979e-108">Requirements</span></span>  
 <span data-ttu-id="f979e-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f979e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f979e-110">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="f979e-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f979e-111">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f979e-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="f979e-112">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="f979e-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f979e-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f979e-113">See also</span></span>

- [<span data-ttu-id="f979e-114">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="f979e-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="f979e-115">Enumerações Fusion</span><span class="sxs-lookup"><span data-stu-id="f979e-115">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
