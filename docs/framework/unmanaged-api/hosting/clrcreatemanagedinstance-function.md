---
title: Função ClrCreateManagedInstance
ms.date: 03/30/2017
api_name:
- ClrCreateManagedInstance
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- ClrCreateManagedInstance
helpviewer_keywords:
- ClrCreateManagedInstance function [.NET Framework hosting]
ms.assetid: 58ba42c0-4857-43bf-a039-73a4dc6544c2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f82303a3d38e7a5baaf1c3edcc41518228360d34
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59088451"
---
# <a name="clrcreatemanagedinstance-function"></a><span data-ttu-id="16d0f-102">Função ClrCreateManagedInstance</span><span class="sxs-lookup"><span data-stu-id="16d0f-102">ClrCreateManagedInstance Function</span></span>
<span data-ttu-id="16d0f-103">Cria uma instância do tipo gerenciado especificado.</span><span class="sxs-lookup"><span data-stu-id="16d0f-103">Creates an instance of the specified managed type.</span></span>  
  
 <span data-ttu-id="16d0f-104">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="16d0f-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="16d0f-105">Usar ativação COM para criar uma instância do tipo gerenciado, ou usar a hospedagem (consulte [CLR hospedando Interfaces adicionadas no .NET Framework 4 e 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span><span class="sxs-lookup"><span data-stu-id="16d0f-105">Use COM activation to create an instance of the managed type, or use hosting (see [CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16d0f-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="16d0f-106">Syntax</span></span>  
  
```  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,   
    [in]  REFIID   riid,   
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16d0f-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="16d0f-107">Parameters</span></span>  
 `pTypeName`  
 <span data-ttu-id="16d0f-108">[in] Um ponteiro para o nome do tipo de instância que está sendo solicitado.</span><span class="sxs-lookup"><span data-stu-id="16d0f-108">[in] A pointer to the name of the instance type being requested.</span></span>  
  
 `riid`  
 <span data-ttu-id="16d0f-109">[in] O `IID` do tipo de instância que está sendo solicitado.</span><span class="sxs-lookup"><span data-stu-id="16d0f-109">[in] The `IID` of the instance type being requested.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="16d0f-110">[out] Um ponteiro para um ponteiro para uma instância do tipo gerenciado que foi solicitada pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="16d0f-110">[out] A pointer to a pointer to an instance of the managed type that was requested by the caller.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16d0f-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="16d0f-111">Remarks</span></span>  
 <span data-ttu-id="16d0f-112">O common language runtime já deve ser carregado em um processo.</span><span class="sxs-lookup"><span data-stu-id="16d0f-112">The common language runtime should already be loaded into a process.</span></span> <span data-ttu-id="16d0f-113">Por exemplo, pode ser carregado por meio de uma chamada para o [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) funcionar antes do `ClrCreateManagedInstance` função é chamada.</span><span class="sxs-lookup"><span data-stu-id="16d0f-113">For example, it can be loaded by using a call to the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function before the `ClrCreateManagedInstance` function is called.</span></span> <span data-ttu-id="16d0f-114">Se o tempo de execução não estiver carregado, `ClrCreateManagedInstance` primeiro tenta carregar v1.0.3705 do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="16d0f-114">If the runtime is not loaded, `ClrCreateManagedInstance` first tries to load v1.0.3705 of the runtime.</span></span> <span data-ttu-id="16d0f-115">Se isso falhar, ele tenta carregar a versão mais recente do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="16d0f-115">If that fails, it attempts to load the latest version of the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16d0f-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="16d0f-116">Requirements</span></span>  
 <span data-ttu-id="16d0f-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16d0f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16d0f-118">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="16d0f-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="16d0f-119">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="16d0f-119">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="16d0f-120">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="16d0f-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="16d0f-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16d0f-121">See also</span></span>

- [<span data-ttu-id="16d0f-122">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="16d0f-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="16d0f-123">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="16d0f-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
