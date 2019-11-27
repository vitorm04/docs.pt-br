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
ms.openlocfilehash: 2ccc038b4420040779dae70f15e3a8827ba94180
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444110"
---
# <a name="coinitiee-enumeration"></a><span data-ttu-id="80392-102">Enumeração COINITIEE</span><span class="sxs-lookup"><span data-stu-id="80392-102">COINITIEE Enumeration</span></span>
<span data-ttu-id="80392-103">Especifica constantes usadas por [CoInitialize](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) ao inicializar o Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="80392-103">Specifies constants used by [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80392-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="80392-104">Syntax</span></span>  
  
```cpp  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="80392-105">Membros</span><span class="sxs-lookup"><span data-stu-id="80392-105">Members</span></span>  
  
|<span data-ttu-id="80392-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="80392-106">Member</span></span>|<span data-ttu-id="80392-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="80392-107">Description</span></span>|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|<span data-ttu-id="80392-108">Modo de inicialização padrão.</span><span class="sxs-lookup"><span data-stu-id="80392-108">Default initialization mode.</span></span> <span data-ttu-id="80392-109">Isso inicializa o tempo de execução e cria o <xref:System.AppDomain>padrão.</span><span class="sxs-lookup"><span data-stu-id="80392-109">This initializes the runtime and creates the default <xref:System.AppDomain>.</span></span>|  
|`COINITEE_DLL`|<span data-ttu-id="80392-110">Inicializa para executar uma DLL gerenciada.</span><span class="sxs-lookup"><span data-stu-id="80392-110">Initializes to run a managed DLL.</span></span>|  
|`COINITEE_MAIN`|<span data-ttu-id="80392-111">Inicializa para executar um EXE gerenciado.</span><span class="sxs-lookup"><span data-stu-id="80392-111">Initializes to run a managed EXE.</span></span> <span data-ttu-id="80392-112">Isso inicializa o tempo de execução, mas não cria o <xref:System.AppDomain>padrão, que é criado após a inserção da rotina principal do EXE.</span><span class="sxs-lookup"><span data-stu-id="80392-112">This initializes the runtime but does not create the default <xref:System.AppDomain>, which is created after entering the main routine of the EXE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="80392-113">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="80392-113">Requirements</span></span>  
 <span data-ttu-id="80392-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80392-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80392-115">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="80392-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="80392-116">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="80392-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="80392-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80392-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80392-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80392-118">See also</span></span>

- [<span data-ttu-id="80392-119">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="80392-119">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
