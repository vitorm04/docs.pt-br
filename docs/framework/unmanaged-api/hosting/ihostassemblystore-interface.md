---
title: Interface IHostAssemblyStore
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore
helpviewer_keywords:
- IHostAssemblyStore interface [.NET Framework hosting]
ms.assetid: cccb650f-abe0-41e2-9fd1-b383788eb1f6
topic_type:
- apiref
ms.openlocfilehash: d7475e2423d4dc6f57e8928514d7991169eef232
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124497"
---
# <a name="ihostassemblystore-interface"></a><span data-ttu-id="2c28c-102">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="2c28c-102">IHostAssemblyStore Interface</span></span>
<span data-ttu-id="2c28c-103">Fornece métodos que permitem que um host carregue assemblies e módulos independentemente do Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="2c28c-103">Provides methods that allow a host to load assemblies and modules independently of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2c28c-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="2c28c-104">Methods</span></span>  
  
|<span data-ttu-id="2c28c-105">Método</span><span class="sxs-lookup"><span data-stu-id="2c28c-105">Method</span></span>|<span data-ttu-id="2c28c-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="2c28c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2c28c-107">Método ProvideAssembly</span><span class="sxs-lookup"><span data-stu-id="2c28c-107">ProvideAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|<span data-ttu-id="2c28c-108">Obtém uma referência a um assembly que não é referenciado pelo [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) retornado de uma chamada para [IHostAssemblyManager:: GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="2c28c-108">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) returned from a call to [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span>|  
|[<span data-ttu-id="2c28c-109">Método ProvideModule</span><span class="sxs-lookup"><span data-stu-id="2c28c-109">ProvideModule Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)|<span data-ttu-id="2c28c-110">Resolve um módulo dentro de um assembly ou um arquivo de recurso vinculado (não incorporado).</span><span class="sxs-lookup"><span data-stu-id="2c28c-110">Resolves a module within an assembly or a linked (not embedded) resource file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c28c-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="2c28c-111">Remarks</span></span>  
 <span data-ttu-id="2c28c-112">`IHostAssemblyStore` fornece uma maneira para um host carregar assemblies com eficiência com base na identidade do assembly.</span><span class="sxs-lookup"><span data-stu-id="2c28c-112">`IHostAssemblyStore` provides a way for a host to load assemblies efficiently based on assembly identity.</span></span> <span data-ttu-id="2c28c-113">O host carrega assemblies retornando `IStream` instâncias que apontam diretamente nos bytes.</span><span class="sxs-lookup"><span data-stu-id="2c28c-113">The host loads assemblies by returning `IStream` instances that point directly at the bytes.</span></span>  
  
 <span data-ttu-id="2c28c-114">O CLR determina se um host implementou `IHostAssemblyStore` chamando `IHostAssemblyManager::GetNonHostAssemblyStores` na inicialização.</span><span class="sxs-lookup"><span data-stu-id="2c28c-114">The CLR determines whether a host has implemented `IHostAssemblyStore` by calling `IHostAssemblyManager::GetNonHostAssemblyStores` upon initialization.</span></span> <span data-ttu-id="2c28c-115">Isso permite que o host, por exemplo, controle a associação a assemblies de usuário, mas dependa do tempo de execução para associar a assemblies de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2c28c-115">This allows the host, for example, to control binding to user assemblies, but to rely on the runtime to bind to .NET Framework assemblies.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2c28c-116">No fornecimento de uma implementação de `IHostAssemblyStore`, o host especifica sua intenção de resolver todos os assemblies que não são referenciados pelo `ICLRAssemblyReferenceList` retornado de `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span><span class="sxs-lookup"><span data-stu-id="2c28c-116">In providing an implementation of `IHostAssemblyStore`, the host specifies its intent to resolve all assemblies that are not referenced by the `ICLRAssemblyReferenceList` returned from `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2c28c-117">A versão 2,0 do .NET Framework não fornece uma maneira para o host carregar a imagem nativa de um assembly, conforme fornecido pelo utilitário do [gerador de imagem nativa (NGen. exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) .</span><span class="sxs-lookup"><span data-stu-id="2c28c-117">The .NET Framework version 2.0 does not provide a way for the host to load the native image of an assembly, as provided by the [Native Image Generator (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) utility.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c28c-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2c28c-118">Requirements</span></span>  
 <span data-ttu-id="2c28c-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c28c-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c28c-120">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2c28c-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2c28c-121">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2c28c-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2c28c-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c28c-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c28c-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2c28c-123">See also</span></span>

- [<span data-ttu-id="2c28c-124">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="2c28c-124">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="2c28c-125">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="2c28c-125">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="2c28c-126">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="2c28c-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
