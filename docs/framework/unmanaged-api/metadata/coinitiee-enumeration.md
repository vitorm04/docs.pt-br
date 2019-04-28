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
ms.openlocfilehash: 4a84fdfdba96c58671302c723b8a56848b70eb60
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984120"
---
# <a name="coinitiee-enumeration"></a><span data-ttu-id="e03fb-102">Enumeração COINITIEE</span><span class="sxs-lookup"><span data-stu-id="e03fb-102">COINITIEE Enumeration</span></span>
<span data-ttu-id="e03fb-103">Especifica as constantes usadas pelo [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) ao inicializar o common language runtime.</span><span class="sxs-lookup"><span data-stu-id="e03fb-103">Specifies constants used by [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e03fb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e03fb-104">Syntax</span></span>  
  
```  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="e03fb-105">Membros</span><span class="sxs-lookup"><span data-stu-id="e03fb-105">Members</span></span>  
  
|<span data-ttu-id="e03fb-106">Membro</span><span class="sxs-lookup"><span data-stu-id="e03fb-106">Member</span></span>|<span data-ttu-id="e03fb-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e03fb-107">Description</span></span>|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|<span data-ttu-id="e03fb-108">Modo de inicialização padrão.</span><span class="sxs-lookup"><span data-stu-id="e03fb-108">Default initialization mode.</span></span> <span data-ttu-id="e03fb-109">Isso inicializa o tempo de execução e cria o padrão <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="e03fb-109">This initializes the runtime and creates the default <xref:System.AppDomain>.</span></span>|  
|`COINITEE_DLL`|<span data-ttu-id="e03fb-110">Inicializa para executar uma DLL gerenciada.</span><span class="sxs-lookup"><span data-stu-id="e03fb-110">Initializes to run a managed DLL.</span></span>|  
|`COINITEE_MAIN`|<span data-ttu-id="e03fb-111">Inicializa para executar um arquivo EXE gerenciado.</span><span class="sxs-lookup"><span data-stu-id="e03fb-111">Initializes to run a managed EXE.</span></span> <span data-ttu-id="e03fb-112">Isso inicializa o tempo de execução, mas não cria o padrão <xref:System.AppDomain>, que é criado depois de inserir a rotina do EXE principal.</span><span class="sxs-lookup"><span data-stu-id="e03fb-112">This initializes the runtime but does not create the default <xref:System.AppDomain>, which is created after entering the main routine of the EXE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e03fb-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e03fb-113">Requirements</span></span>  
 <span data-ttu-id="e03fb-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e03fb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e03fb-115">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e03fb-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e03fb-116">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e03fb-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e03fb-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e03fb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e03fb-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e03fb-118">See also</span></span>

- [<span data-ttu-id="e03fb-119">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="e03fb-119">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
