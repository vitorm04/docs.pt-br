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
ms.openlocfilehash: cca73eec663b9afd12ecea5ab9d7073ea0168d33
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501549"
---
# <a name="ihostassemblystore-interface"></a><span data-ttu-id="00734-102">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="00734-102">IHostAssemblyStore Interface</span></span>
<span data-ttu-id="00734-103">Fornece métodos que permitem que um host carregue assemblies e módulos independentemente do Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="00734-103">Provides methods that allow a host to load assemblies and modules independently of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="00734-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="00734-104">Methods</span></span>  
  
|<span data-ttu-id="00734-105">Método</span><span class="sxs-lookup"><span data-stu-id="00734-105">Method</span></span>|<span data-ttu-id="00734-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="00734-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="00734-107">Método ProvideAssembly</span><span class="sxs-lookup"><span data-stu-id="00734-107">ProvideAssembly Method</span></span>](ihostassemblystore-provideassembly-method.md)|<span data-ttu-id="00734-108">Obtém uma referência a um assembly que não é referenciado pelo [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) retornado de uma chamada para [IHostAssemblyManager:: GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="00734-108">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) returned from a call to [IHostAssemblyManager::GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span>|  
|[<span data-ttu-id="00734-109">Método ProvideModule</span><span class="sxs-lookup"><span data-stu-id="00734-109">ProvideModule Method</span></span>](ihostassemblystore-providemodule-method.md)|<span data-ttu-id="00734-110">Resolve um módulo dentro de um assembly ou um arquivo de recurso vinculado (não incorporado).</span><span class="sxs-lookup"><span data-stu-id="00734-110">Resolves a module within an assembly or a linked (not embedded) resource file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00734-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="00734-111">Remarks</span></span>  
 <span data-ttu-id="00734-112">`IHostAssemblyStore`fornece uma maneira para um host carregar assemblies com eficiência com base na identidade do assembly.</span><span class="sxs-lookup"><span data-stu-id="00734-112">`IHostAssemblyStore` provides a way for a host to load assemblies efficiently based on assembly identity.</span></span> <span data-ttu-id="00734-113">O host carrega assemblies retornando `IStream` instâncias que apontam diretamente nos bytes.</span><span class="sxs-lookup"><span data-stu-id="00734-113">The host loads assemblies by returning `IStream` instances that point directly at the bytes.</span></span>  
  
 <span data-ttu-id="00734-114">O CLR determina se um host foi implementado `IHostAssemblyStore` chamando `IHostAssemblyManager::GetNonHostAssemblyStores` na inicialização.</span><span class="sxs-lookup"><span data-stu-id="00734-114">The CLR determines whether a host has implemented `IHostAssemblyStore` by calling `IHostAssemblyManager::GetNonHostAssemblyStores` upon initialization.</span></span> <span data-ttu-id="00734-115">Isso permite que o host, por exemplo, controle a associação a assemblies de usuário, mas dependa do tempo de execução para associar a assemblies de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="00734-115">This allows the host, for example, to control binding to user assemblies, but to rely on the runtime to bind to .NET Framework assemblies.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="00734-116">No fornecimento de uma implementação do `IHostAssemblyStore` , o host especifica sua intenção de resolver todos os assemblies que não são referenciados pelo `ICLRAssemblyReferenceList` retornado de `IHostAssemblyManager::GetNonHostStoreAssemblies` .</span><span class="sxs-lookup"><span data-stu-id="00734-116">In providing an implementation of `IHostAssemblyStore`, the host specifies its intent to resolve all assemblies that are not referenced by the `ICLRAssemblyReferenceList` returned from `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="00734-117">A versão 2,0 do .NET Framework não fornece uma maneira para o host carregar a imagem nativa de um assembly, conforme fornecido pelo utilitário do [gerador de imagem nativa (NGen. exe)](../../tools/ngen-exe-native-image-generator.md) .</span><span class="sxs-lookup"><span data-stu-id="00734-117">The .NET Framework version 2.0 does not provide a way for the host to load the native image of an assembly, as provided by the [Native Image Generator (Ngen.exe)](../../tools/ngen-exe-native-image-generator.md) utility.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00734-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="00734-118">Requirements</span></span>  
 <span data-ttu-id="00734-119">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00734-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00734-120">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="00734-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="00734-121">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="00734-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="00734-122">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00734-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00734-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="00734-123">See also</span></span>

- [<span data-ttu-id="00734-124">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="00734-124">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="00734-125">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="00734-125">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="00734-126">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="00734-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
