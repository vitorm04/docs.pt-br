---
title: Enumeração COINITIEE
ms.date: 03/30/2017
api_name:
- COINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COINITIEE
helpviewer_keywords:
- COINITIEE enumeration [.NET Framework metadata]
ms.assetid: 64264238-3b68-4bac-a887-36b552426a6c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 48f15cc08167baaadc61787b8b1f7167304f0cae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569473"
---
# <a name="coinitiee-enumeration"></a><span data-ttu-id="db34e-102">Enumeração COINITIEE</span><span class="sxs-lookup"><span data-stu-id="db34e-102">COINITIEE Enumeration</span></span>
<span data-ttu-id="db34e-103">Especifica as constantes usadas pelo [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) ao inicializar o common language runtime.</span><span class="sxs-lookup"><span data-stu-id="db34e-103">Specifies constants used by [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db34e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="db34e-104">Syntax</span></span>  
  
```  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="db34e-105">Membros</span><span class="sxs-lookup"><span data-stu-id="db34e-105">Members</span></span>  
  
|<span data-ttu-id="db34e-106">Membro</span><span class="sxs-lookup"><span data-stu-id="db34e-106">Member</span></span>|<span data-ttu-id="db34e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="db34e-107">Description</span></span>|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|<span data-ttu-id="db34e-108">Modo de inicialização padrão.</span><span class="sxs-lookup"><span data-stu-id="db34e-108">Default initialization mode.</span></span> <span data-ttu-id="db34e-109">Isso inicializa o tempo de execução e cria o padrão <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="db34e-109">This initializes the runtime and creates the default <xref:System.AppDomain>.</span></span>|  
|`COINITEE_DLL`|<span data-ttu-id="db34e-110">Inicializa para executar uma DLL gerenciada.</span><span class="sxs-lookup"><span data-stu-id="db34e-110">Initializes to run a managed DLL.</span></span>|  
|`COINITEE_MAIN`|<span data-ttu-id="db34e-111">Inicializa para executar um arquivo EXE gerenciado.</span><span class="sxs-lookup"><span data-stu-id="db34e-111">Initializes to run a managed EXE.</span></span> <span data-ttu-id="db34e-112">Isso inicializa o tempo de execução, mas não cria o padrão <xref:System.AppDomain>, que é criado depois de inserir a rotina do EXE principal.</span><span class="sxs-lookup"><span data-stu-id="db34e-112">This initializes the runtime but does not create the default <xref:System.AppDomain>, which is created after entering the main routine of the EXE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="db34e-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="db34e-113">Requirements</span></span>  
 <span data-ttu-id="db34e-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db34e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db34e-115">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="db34e-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="db34e-116">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="db34e-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="db34e-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db34e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db34e-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db34e-118">See also</span></span>
- [<span data-ttu-id="db34e-119">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="db34e-119">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
