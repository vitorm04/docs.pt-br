---
title: "Interoperação com código não gerenciado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- unmanaged code, interoperation
- managed code, interoperation with unmanaged code
- .NET Framework, interoperation with unmanaged code
- unmanaged code
- interoperation with unmanaged code
- interoperation with unmanaged code, about interoperation
- components [.NET Framework], interoperation with unmanaged code
ms.assetid: ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258
caps.latest.revision: 15
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ff86b062efddde6f97555efb97247f60a6e1db98
ms.contentlocale: pt-br
ms.lasthandoff: 09/08/2017

---
# <a name="interoperating-with-unmanaged-code"></a><span data-ttu-id="1b8a0-102">Interoperação com código não gerenciado</span><span class="sxs-lookup"><span data-stu-id="1b8a0-102">Interoperating with Unmanaged Code</span></span>
<span data-ttu-id="1b8a0-103">O .NET Framework promove a interação com componentes COM, serviços COM+, bibliotecas de tipos externas e muitos serviços do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="1b8a0-103">The .NET Framework promotes interaction with COM components, COM+ services, external type libraries, and many operating system services.</span></span> <span data-ttu-id="1b8a0-104">Tipos de dados, assinaturas de método e mecanismos de tratamento de erros variam entre modelos de objetos gerenciados e não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="1b8a0-104">Data types, method signatures, and error-handling mechanisms vary between managed and unmanaged object models.</span></span> <span data-ttu-id="1b8a0-105">Para simplificar a interoperação entre componentes do .NET Framework e o código não gerenciado e para facilitar o caminho de migração, o Common Language Runtime oculta de clientes e servidores as diferenças entre esses modelos de objeto.</span><span class="sxs-lookup"><span data-stu-id="1b8a0-105">To simplify interoperation between .NET Framework components and unmanaged code and to ease the migration path, the common language runtime conceals from both clients and servers the differences in these object models.</span></span>  
  
 <span data-ttu-id="1b8a0-106">O código que é executado sob o controle de tempo de execução é chamado de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="1b8a0-106">Code that executes under the control of the runtime is called managed code.</span></span> <span data-ttu-id="1b8a0-107">Em contraste, o código executado fora do tempo de execução é chamado de código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="1b8a0-107">Conversely, code that runs outside the runtime is called unmanaged code.</span></span> <span data-ttu-id="1b8a0-108">Componentes COM, interfaces ActiveX e funções da API do Win32 são exemplos de código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="1b8a0-108">COM components, ActiveX interfaces, and Win32 API functions are examples of unmanaged code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1b8a0-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="1b8a0-109">In This Section</span></span>  
 [<span data-ttu-id="1b8a0-110">Tópicos explicativos sobre interoperação com código não gerenciado</span><span class="sxs-lookup"><span data-stu-id="1b8a0-110">Interoperating with Unmanaged Code How-to Topics</span></span>](http://msdn.microsoft.com/en-us/ec21c6e1-e233-4cd9-95ae-b9b9cf807f9d)  
 <span data-ttu-id="1b8a0-111">Fornece links a todos os Tópicos explicativos encontrados na documentação conceitual para interoperação com código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="1b8a0-111">Provides links to all How-to topics found in the conceptual documentation for interoperating with unmanaged code.</span></span>  
  
 [<span data-ttu-id="1b8a0-112">Expondo componentes do COM ao .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1b8a0-112">Exposing COM Components to the .NET Framework</span></span>](../../../docs/framework/interop/exposing-com-components.md)  
 <span data-ttu-id="1b8a0-113">Descreve como usar componentes COM de aplicativos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1b8a0-113">Describes how to use COM components from .NET Framework applications.</span></span>  
  
 [<span data-ttu-id="1b8a0-114">Expondo componentes do .NET Framework ao COM</span><span class="sxs-lookup"><span data-stu-id="1b8a0-114">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 <span data-ttu-id="1b8a0-115">Descreve como usar componentes do .NET Framework de aplicativos COM.</span><span class="sxs-lookup"><span data-stu-id="1b8a0-115">Describes how to use .NET Framework components from COM applications.</span></span>  
  
 [<span data-ttu-id="1b8a0-116">Consumindo funções de DLL não gerenciadas</span><span class="sxs-lookup"><span data-stu-id="1b8a0-116">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 <span data-ttu-id="1b8a0-117">Descreve como chamar funções de DLL não gerenciadas usando a invocação de plataforma.</span><span class="sxs-lookup"><span data-stu-id="1b8a0-117">Describes how to call unmanaged DLL functions using platform invoke.</span></span>  
  
 [<span data-ttu-id="1b8a0-118">Considerações sobre design para interoperação</span><span class="sxs-lookup"><span data-stu-id="1b8a0-118">Design Considerations for Interoperation</span></span>](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689)  
 <span data-ttu-id="1b8a0-119">Fornece dicas para escrever componentes COM integrados.</span><span class="sxs-lookup"><span data-stu-id="1b8a0-119">Provides tips for writing integrated COM components.</span></span>  
  
 [<span data-ttu-id="1b8a0-120">Marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="1b8a0-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)  
 <span data-ttu-id="1b8a0-121">Descreve o marshaling para invocação de plataforma e interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="1b8a0-121">Describes marshaling for COM interop and platform invoke.</span></span>  
  
 [<span data-ttu-id="1b8a0-122">Como mapear HRESULTs e exceções</span><span class="sxs-lookup"><span data-stu-id="1b8a0-122">How to: Map HRESULTs and Exceptions</span></span>](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md)  
 <span data-ttu-id="1b8a0-123">Descreve o mapeamento entre exceções e HRESULTs.</span><span class="sxs-lookup"><span data-stu-id="1b8a0-123">Describes the mapping between exceptions and HRESULTs.</span></span>  
  
 [<span data-ttu-id="1b8a0-124">Interoperação usando tipos genéricos</span><span class="sxs-lookup"><span data-stu-id="1b8a0-124">Interoperating Using Generic Types</span></span>](http://msdn.microsoft.com/en-us/26b88e03-085b-4b53-94ba-a5a9c709ce58)  
 <span data-ttu-id="1b8a0-125">Descreve o comportamento de tipos genéricos quando usados em interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="1b8a0-125">Describes the behavior of generic types when used in COM interop.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1b8a0-126">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="1b8a0-126">Related Sections</span></span>  
 [<span data-ttu-id="1b8a0-127">Interoperabilidade COM avançada</span><span class="sxs-lookup"><span data-stu-id="1b8a0-127">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 <span data-ttu-id="1b8a0-128">Fornece links para obter mais informações sobre como incorporar componentes COM no aplicativo do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1b8a0-128">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>

