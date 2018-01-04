---
title: "Enumeração COINITIEE"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COINITIEE
api_location: mscoree.dll
api_type: COM
f1_keywords: COINITIEE
helpviewer_keywords: COINITIEE enumeration [.NET Framework metadata]
ms.assetid: 64264238-3b68-4bac-a887-36b552426a6c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ad117c3efd31cc176281e571b7fde11229c097e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="coinitiee-enumeration"></a><span data-ttu-id="2f817-102">Enumeração COINITIEE</span><span class="sxs-lookup"><span data-stu-id="2f817-102">COINITIEE Enumeration</span></span>
<span data-ttu-id="2f817-103">Especifica constantes usadas pelo [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) ao inicializar o common language runtime.</span><span class="sxs-lookup"><span data-stu-id="2f817-103">Specifies constants used by [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f817-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2f817-104">Syntax</span></span>  
  
```  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="2f817-105">Membros</span><span class="sxs-lookup"><span data-stu-id="2f817-105">Members</span></span>  
  
|<span data-ttu-id="2f817-106">Membro</span><span class="sxs-lookup"><span data-stu-id="2f817-106">Member</span></span>|<span data-ttu-id="2f817-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2f817-107">Description</span></span>|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|<span data-ttu-id="2f817-108">Modo de inicialização padrão.</span><span class="sxs-lookup"><span data-stu-id="2f817-108">Default initialization mode.</span></span> <span data-ttu-id="2f817-109">Isso inicializa o tempo de execução e cria o padrão <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="2f817-109">This initializes the runtime and creates the default <xref:System.AppDomain>.</span></span>|  
|`COINITEE_DLL`|<span data-ttu-id="2f817-110">Inicializa para executar uma DLL gerenciada.</span><span class="sxs-lookup"><span data-stu-id="2f817-110">Initializes to run a managed DLL.</span></span>|  
|`COINITEE_MAIN`|<span data-ttu-id="2f817-111">Inicializa para executar um. EXE gerenciado.</span><span class="sxs-lookup"><span data-stu-id="2f817-111">Initializes to run a managed EXE.</span></span> <span data-ttu-id="2f817-112">Isso inicializa o tempo de execução, mas não cria o padrão <xref:System.AppDomain>, que é criado depois de inserir a rotina principal do executável.</span><span class="sxs-lookup"><span data-stu-id="2f817-112">This initializes the runtime but does not create the default <xref:System.AppDomain>, which is created after entering the main routine of the EXE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2f817-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2f817-113">Requirements</span></span>  
 <span data-ttu-id="2f817-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f817-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f817-115">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2f817-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2f817-116">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="2f817-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2f817-117">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f817-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f817-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2f817-118">See Also</span></span>  
 [<span data-ttu-id="2f817-119">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="2f817-119">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
