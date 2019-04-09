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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4067c1fbcf99c903c892eaec58262d95569114b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59173414"
---
# <a name="ihostassemblystore-interface"></a><span data-ttu-id="440eb-102">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="440eb-102">IHostAssemblyStore Interface</span></span>
<span data-ttu-id="440eb-103">Fornece métodos que permitem que um host carregar assemblies e módulos independentemente do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="440eb-103">Provides methods that allow a host to load assemblies and modules independently of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="440eb-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="440eb-104">Methods</span></span>  
  
|<span data-ttu-id="440eb-105">Método</span><span class="sxs-lookup"><span data-stu-id="440eb-105">Method</span></span>|<span data-ttu-id="440eb-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="440eb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="440eb-107">Método ProvideAssembly</span><span class="sxs-lookup"><span data-stu-id="440eb-107">ProvideAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|<span data-ttu-id="440eb-108">Obtém uma referência a um assembly que não é referenciado pela [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) retornado de uma chamada para [ihostassemblymanager:: Getnonhoststoreassemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="440eb-108">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) returned from a call to [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span>|  
|[<span data-ttu-id="440eb-109">Método ProvideModule</span><span class="sxs-lookup"><span data-stu-id="440eb-109">ProvideModule Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)|<span data-ttu-id="440eb-110">Resolve um módulo dentro de um assembly ou um arquivo de recurso (não inserido) vinculado.</span><span class="sxs-lookup"><span data-stu-id="440eb-110">Resolves a module within an assembly or a linked (not embedded) resource file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="440eb-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="440eb-111">Remarks</span></span>  
 `IHostAssemblyStore` <span data-ttu-id="440eb-112">Fornece uma maneira para um host carregar assemblies com eficiência com base na identidade do assembly.</span><span class="sxs-lookup"><span data-stu-id="440eb-112">provides a way for a host to load assemblies efficiently based on assembly identity.</span></span> <span data-ttu-id="440eb-113">O host carrega assemblies, retornando `IStream` instâncias que apontam diretamente para os bytes.</span><span class="sxs-lookup"><span data-stu-id="440eb-113">The host loads assemblies by returning `IStream` instances that point directly at the bytes.</span></span>  
  
 <span data-ttu-id="440eb-114">O CLR determina se um host tiver implementado `IHostAssemblyStore` chamando `IHostAssemblyManager::GetNonHostAssemblyStores` na inicialização.</span><span class="sxs-lookup"><span data-stu-id="440eb-114">The CLR determines whether a host has implemented `IHostAssemblyStore` by calling `IHostAssemblyManager::GetNonHostAssemblyStores` upon initialization.</span></span> <span data-ttu-id="440eb-115">Isso permite que o host, por exemplo, para controlar a associação para assemblies de usuário, mas contar com o tempo de execução para associar aos assemblies do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="440eb-115">This allows the host, for example, to control binding to user assemblies, but to rely on the runtime to bind to .NET Framework assemblies.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="440eb-116">No fornecimento de uma implementação de `IHostAssemblyStore`, o host especifica sua intenção de resolver todos os assemblies que não são referenciados pela `ICLRAssemblyReferenceList` retornados de `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span><span class="sxs-lookup"><span data-stu-id="440eb-116">In providing an implementation of `IHostAssemblyStore`, the host specifies its intent to resolve all assemblies that are not referenced by the `ICLRAssemblyReferenceList` returned from `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="440eb-117">O .NET Framework versão 2.0 não fornece uma maneira para o host carregar a imagem nativa de um assembly, conforme fornecido pelo [gerador de imagem nativa (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) utilitário.</span><span class="sxs-lookup"><span data-stu-id="440eb-117">The .NET Framework version 2.0 does not provide a way for the host to load the native image of an assembly, as provided by the [Native Image Generator (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) utility.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="440eb-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="440eb-118">Requirements</span></span>  
 <span data-ttu-id="440eb-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="440eb-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="440eb-120">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="440eb-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="440eb-121">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="440eb-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="440eb-122">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="440eb-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="440eb-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="440eb-123">See also</span></span>

- [<span data-ttu-id="440eb-124">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="440eb-124">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="440eb-125">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="440eb-125">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="440eb-126">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="440eb-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
