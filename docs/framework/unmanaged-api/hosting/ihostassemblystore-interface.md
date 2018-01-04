---
title: Interface IHostAssemblyStore
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAssemblyStore
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAssemblyStore
helpviewer_keywords: IHostAssemblyStore interface [.NET Framework hosting]
ms.assetid: cccb650f-abe0-41e2-9fd1-b383788eb1f6
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c795d4baa3030817299f23c3dadf4caf7a5edc5a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostassemblystore-interface"></a><span data-ttu-id="1e59a-102">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="1e59a-102">IHostAssemblyStore Interface</span></span>
<span data-ttu-id="1e59a-103">Fornece métodos que permitem que um host ao carregar assemblies e módulos independentemente do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="1e59a-103">Provides methods that allow a host to load assemblies and modules independently of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1e59a-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="1e59a-104">Methods</span></span>  
  
|<span data-ttu-id="1e59a-105">Método</span><span class="sxs-lookup"><span data-stu-id="1e59a-105">Method</span></span>|<span data-ttu-id="1e59a-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="1e59a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1e59a-107">Método ProvideAssembly</span><span class="sxs-lookup"><span data-stu-id="1e59a-107">ProvideAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|<span data-ttu-id="1e59a-108">Obtém uma referência a um assembly que não é referenciado pelo [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) retornado de uma chamada para [Ihostassemblymanager](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="1e59a-108">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) returned from a call to [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span>|  
|[<span data-ttu-id="1e59a-109">Método ProvideModule</span><span class="sxs-lookup"><span data-stu-id="1e59a-109">ProvideModule Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)|<span data-ttu-id="1e59a-110">Resolve um módulo dentro de um assembly ou um arquivo de recurso (não inserido) vinculado.</span><span class="sxs-lookup"><span data-stu-id="1e59a-110">Resolves a module within an assembly or a linked (not embedded) resource file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e59a-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="1e59a-111">Remarks</span></span>  
 <span data-ttu-id="1e59a-112">`IHostAssemblyStore`Fornece uma maneira para um host carregar assemblies com eficiência com base na identidade do assembly.</span><span class="sxs-lookup"><span data-stu-id="1e59a-112">`IHostAssemblyStore` provides a way for a host to load assemblies efficiently based on assembly identity.</span></span> <span data-ttu-id="1e59a-113">O host carrega assemblies retornando `IStream` instâncias que aponte diretamente para os bytes.</span><span class="sxs-lookup"><span data-stu-id="1e59a-113">The host loads assemblies by returning `IStream` instances that point directly at the bytes.</span></span>  
  
 <span data-ttu-id="1e59a-114">O CLR determina se um host tiver implementado `IHostAssemblyStore` chamando `IHostAssemblyManager::GetNonHostAssemblyStores` na inicialização.</span><span class="sxs-lookup"><span data-stu-id="1e59a-114">The CLR determines whether a host has implemented `IHostAssemblyStore` by calling `IHostAssemblyManager::GetNonHostAssemblyStores` upon initialization.</span></span> <span data-ttu-id="1e59a-115">Isso permite que o host, por exemplo, para controlar a associação para assemblies de usuário, mas a contar com o tempo de execução para associar a assemblies do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1e59a-115">This allows the host, for example, to control binding to user assemblies, but to rely on the runtime to bind to .NET Framework assemblies.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e59a-116">Fornecer uma implementação de `IHostAssemblyStore`, o host especifica sua intenção de resolver todos os assemblies que não são referenciados pelo `ICLRAssemblyReferenceList` retornado de `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span><span class="sxs-lookup"><span data-stu-id="1e59a-116">In providing an implementation of `IHostAssemblyStore`, the host specifies its intent to resolve all assemblies that are not referenced by the `ICLRAssemblyReferenceList` returned from `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e59a-117">O .NET Framework versão 2.0 não oferece uma maneira para o host carregar a imagem nativa de um assembly, conforme fornecido pelo [gerador de imagem nativa (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) utilitário.</span><span class="sxs-lookup"><span data-stu-id="1e59a-117">The .NET Framework version 2.0 does not provide a way for the host to load the native image of an assembly, as provided by the [Native Image Generator (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) utility.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e59a-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1e59a-118">Requirements</span></span>  
 <span data-ttu-id="1e59a-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e59a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e59a-120">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1e59a-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1e59a-121">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="1e59a-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1e59a-122">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e59a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e59a-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1e59a-123">See Also</span></span>  
 [<span data-ttu-id="1e59a-124">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="1e59a-124">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="1e59a-125">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="1e59a-125">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="1e59a-126">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="1e59a-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
