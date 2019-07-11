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
ms.openlocfilehash: e1ae530b8488dcd375e91058a227316dd38cf4ab
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779165"
---
# <a name="clrcreatemanagedinstance-function"></a><span data-ttu-id="d7cc3-102">Função ClrCreateManagedInstance</span><span class="sxs-lookup"><span data-stu-id="d7cc3-102">ClrCreateManagedInstance Function</span></span>
<span data-ttu-id="d7cc3-103">Cria uma instância do tipo gerenciado especificado.</span><span class="sxs-lookup"><span data-stu-id="d7cc3-103">Creates an instance of the specified managed type.</span></span>  
  
 <span data-ttu-id="d7cc3-104">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d7cc3-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="d7cc3-105">Usar ativação COM para criar uma instância do tipo gerenciado, ou usar a hospedagem (consulte [CLR hospedando Interfaces adicionadas no .NET Framework 4 e 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span><span class="sxs-lookup"><span data-stu-id="d7cc3-105">Use COM activation to create an instance of the managed type, or use hosting (see [CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7cc3-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d7cc3-106">Syntax</span></span>  
  
```cpp  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,   
    [in]  REFIID   riid,   
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7cc3-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d7cc3-107">Parameters</span></span>  
 `pTypeName`  
 <span data-ttu-id="d7cc3-108">[in] Um ponteiro para o nome do tipo de instância que está sendo solicitado.</span><span class="sxs-lookup"><span data-stu-id="d7cc3-108">[in] A pointer to the name of the instance type being requested.</span></span>  
  
 `riid`  
 <span data-ttu-id="d7cc3-109">[in] O `IID` do tipo de instância que está sendo solicitado.</span><span class="sxs-lookup"><span data-stu-id="d7cc3-109">[in] The `IID` of the instance type being requested.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="d7cc3-110">[out] Um ponteiro para um ponteiro para uma instância do tipo gerenciado que foi solicitada pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="d7cc3-110">[out] A pointer to a pointer to an instance of the managed type that was requested by the caller.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7cc3-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="d7cc3-111">Remarks</span></span>  
 <span data-ttu-id="d7cc3-112">O common language runtime já deve ser carregado em um processo.</span><span class="sxs-lookup"><span data-stu-id="d7cc3-112">The common language runtime should already be loaded into a process.</span></span> <span data-ttu-id="d7cc3-113">Por exemplo, pode ser carregado por meio de uma chamada para o [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) funcionar antes do `ClrCreateManagedInstance` função é chamada.</span><span class="sxs-lookup"><span data-stu-id="d7cc3-113">For example, it can be loaded by using a call to the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function before the `ClrCreateManagedInstance` function is called.</span></span> <span data-ttu-id="d7cc3-114">Se o tempo de execução não estiver carregado, `ClrCreateManagedInstance` primeiro tenta carregar v1.0.3705 do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d7cc3-114">If the runtime is not loaded, `ClrCreateManagedInstance` first tries to load v1.0.3705 of the runtime.</span></span> <span data-ttu-id="d7cc3-115">Se isso falhar, ele tenta carregar a versão mais recente do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d7cc3-115">If that fails, it attempts to load the latest version of the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7cc3-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d7cc3-116">Requirements</span></span>  
 <span data-ttu-id="d7cc3-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7cc3-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7cc3-118">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d7cc3-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d7cc3-119">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d7cc3-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d7cc3-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7cc3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7cc3-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7cc3-121">See also</span></span>

- [<span data-ttu-id="d7cc3-122">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="d7cc3-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="d7cc3-123">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="d7cc3-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
