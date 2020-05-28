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
ms.openlocfilehash: f4d1c2f105abb64bf196d0dd8371c2788c97336e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005902"
---
# <a name="coinitiee-enumeration"></a><span data-ttu-id="9583f-102">Enumeração COINITIEE</span><span class="sxs-lookup"><span data-stu-id="9583f-102">COINITIEE Enumeration</span></span>
<span data-ttu-id="9583f-103">Especifica constantes usadas por [CoInitialize](../hosting/coinitializeee-function.md) ao inicializar o Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="9583f-103">Specifies constants used by [CoInitializeEE](../hosting/coinitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9583f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9583f-104">Syntax</span></span>  
  
```cpp  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="9583f-105">Membros</span><span class="sxs-lookup"><span data-stu-id="9583f-105">Members</span></span>  
  
|<span data-ttu-id="9583f-106">Membro</span><span class="sxs-lookup"><span data-stu-id="9583f-106">Member</span></span>|<span data-ttu-id="9583f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9583f-107">Description</span></span>|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|<span data-ttu-id="9583f-108">Modo de inicialização padrão.</span><span class="sxs-lookup"><span data-stu-id="9583f-108">Default initialization mode.</span></span> <span data-ttu-id="9583f-109">Isso inicializa o tempo de execução e cria o padrão <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="9583f-109">This initializes the runtime and creates the default <xref:System.AppDomain>.</span></span>|  
|`COINITEE_DLL`|<span data-ttu-id="9583f-110">Inicializa para executar uma DLL gerenciada.</span><span class="sxs-lookup"><span data-stu-id="9583f-110">Initializes to run a managed DLL.</span></span>|  
|`COINITEE_MAIN`|<span data-ttu-id="9583f-111">Inicializa para executar um EXE gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9583f-111">Initializes to run a managed EXE.</span></span> <span data-ttu-id="9583f-112">Isso inicializa o tempo de execução, mas não cria o padrão <xref:System.AppDomain> , que é criado após a inserção da rotina principal do exe.</span><span class="sxs-lookup"><span data-stu-id="9583f-112">This initializes the runtime but does not create the default <xref:System.AppDomain>, which is created after entering the main routine of the EXE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9583f-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9583f-113">Requirements</span></span>  
 <span data-ttu-id="9583f-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9583f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9583f-115">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9583f-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9583f-116">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9583f-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9583f-117">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9583f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9583f-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="9583f-118">See also</span></span>

- [<span data-ttu-id="9583f-119">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="9583f-119">Metadata Enumerations</span></span>](metadata-enumerations.md)
