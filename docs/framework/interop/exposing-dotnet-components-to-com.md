---
title: Expondo componentes do .NET Framework para COM
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exposing .NET Framework components to COM
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: e42a65f7-1e61-411f-b09a-aca1bbce24c6
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9451504b64ddaa8dc0ea6b3a0754257b2c8b3824
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="exposing-net-framework-components-to-com"></a><span data-ttu-id="44a60-102">Expondo componentes do .NET Framework para COM</span><span class="sxs-lookup"><span data-stu-id="44a60-102">Exposing .NET Framework Components to COM</span></span>
<span data-ttu-id="44a60-103">A escrita de um tipo .NET e o consumo desse tipo em um código não gerenciado são atividades distintas para desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="44a60-103">Writing a .NET type and consuming that type from unmanaged code are distinct activities for developers.</span></span> <span data-ttu-id="44a60-104">Esta seção descreve várias dicas para escrever um código gerenciado que interopera com clientes COM:</span><span class="sxs-lookup"><span data-stu-id="44a60-104">This section describes several tips for writing managed code that interoperates with COM clients:</span></span>  
  
-   <span data-ttu-id="44a60-105">[Qualificando tipos .NET para interoperação](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="44a60-105">[Qualifying .NET types for interoperation](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).</span></span>  
  
     <span data-ttu-id="44a60-106">Todos os tipos gerenciados, métodos, propriedades, campos e eventos que você deseja expor ao COM devem ser públicos.</span><span class="sxs-lookup"><span data-stu-id="44a60-106">All managed types, methods, properties, fields, and events that you want to expose to COM must be public.</span></span> <span data-ttu-id="44a60-107">Os tipos devem ter um construtor padrão público, que é o único construtor que pode ser invocado por meio do COM.</span><span class="sxs-lookup"><span data-stu-id="44a60-107">Types must have a public default constructor, which is the only constructor that can be invoked through COM.</span></span>  
  
-   <span data-ttu-id="44a60-108">[Aplicando atributos de interoperabilidade](../../../docs/framework/interop/applying-interop-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="44a60-108">[Applying interop attributes](../../../docs/framework/interop/applying-interop-attributes.md).</span></span>  
  
     <span data-ttu-id="44a60-109">Atributos personalizados no código gerenciado podem melhorar a interoperabilidade de um componente.</span><span class="sxs-lookup"><span data-stu-id="44a60-109">Custom attributes within managed code can enhance the interoperability of a component.</span></span>  
  
-   <span data-ttu-id="44a60-110">[Empacotando um assembly para o COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span><span class="sxs-lookup"><span data-stu-id="44a60-110">[Packaging an assembly for COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span></span>  
  
     <span data-ttu-id="44a60-111">Os desenvolvedores do COM podem precisar que você resuma as etapas envolvidas na referência e implantação dos assemblies.</span><span class="sxs-lookup"><span data-stu-id="44a60-111">COM developers might require that you summarize the steps involved in referencing and deploying your assemblies.</span></span>  
  
 <span data-ttu-id="44a60-112">Além disso, esta seção identifica as tarefas relacionadas ao consumo de um tipo gerenciado em um cliente COM.</span><span class="sxs-lookup"><span data-stu-id="44a60-112">Additionally, this section identifies the tasks related to consuming a managed type from a COM client.</span></span>  
  
#### <a name="to-consume-a-managed-type-from-com"></a><span data-ttu-id="44a60-113">Para consumir um tipo gerenciado por meio do COM</span><span class="sxs-lookup"><span data-stu-id="44a60-113">To consume a managed type from COM</span></span>  
  
1.  <span data-ttu-id="44a60-114">[Registrar assemblies com o COM](../../../docs/framework/interop/registering-assemblies-with-com.md).</span><span class="sxs-lookup"><span data-stu-id="44a60-114">[Register assemblies with COM](../../../docs/framework/interop/registering-assemblies-with-com.md).</span></span>  
  
     <span data-ttu-id="44a60-115">Os tipos em um assembly (e as bibliotecas de tipos) devem ser registrados em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="44a60-115">Types in an assembly (and type libraries) must be registered at design time.</span></span> <span data-ttu-id="44a60-116">Se um instalador não registrar o assembly, instrua os desenvolvedores do COM a usar Regasm.exe.</span><span class="sxs-lookup"><span data-stu-id="44a60-116">If an installer does not register the assembly, instruct COM developers to use Regasm.exe.</span></span>  
  
2.  <span data-ttu-id="44a60-117">[Referenciar tipos .NET por meio do COM](../../../docs/framework/interop/how-to-reference-net-types-from-com.md).</span><span class="sxs-lookup"><span data-stu-id="44a60-117">[Reference .NET types from COM](../../../docs/framework/interop/how-to-reference-net-types-from-com.md).</span></span>  
  
     <span data-ttu-id="44a60-118">Os desenvolvedores do COM podem referenciar tipos em um assembly usando as mesmas ferramentas e técnicas que usam hoje.</span><span class="sxs-lookup"><span data-stu-id="44a60-118">COM developers can reference types in an assembly using the same tools and techniques they use today.</span></span>  
  
3.  <span data-ttu-id="44a60-119">[Chamar um objeto .NET](http://msdn.microsoft.com/en-us/40c9626c-aea6-4bad-b8f0-c1de462efd33).</span><span class="sxs-lookup"><span data-stu-id="44a60-119">[Call a .NET object](http://msdn.microsoft.com/en-us/40c9626c-aea6-4bad-b8f0-c1de462efd33).</span></span>  
  
     <span data-ttu-id="44a60-120">Os desenvolvedores do COM podem chamar métodos no objeto .NET da mesma forma que chamam métodos em qualquer tipo não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="44a60-120">COM developers can call methods on the .NET object the same way they call methods on any unmanaged type.</span></span> <span data-ttu-id="44a60-121">Por exemplo, a API **CoCreateInstance** do COM ativa objetos .NET.</span><span class="sxs-lookup"><span data-stu-id="44a60-121">For example, the COM **CoCreateInstance** API activates .NET objects.</span></span>  
  
4.  <span data-ttu-id="44a60-122">[Implante um aplicativo para o acesso COM](http://msdn.microsoft.com/en-us/fb63564c-c1b9-4655-a094-a235625882ce).</span><span class="sxs-lookup"><span data-stu-id="44a60-122">[Deploy an application for COM access](http://msdn.microsoft.com/en-us/fb63564c-c1b9-4655-a094-a235625882ce).</span></span>  
  
     <span data-ttu-id="44a60-123">Um assembly de nome forte pode ser instalado no cache de assembly global e exige uma assinatura de seu fornecedor.</span><span class="sxs-lookup"><span data-stu-id="44a60-123">A strong-named assembly can be installed in the global assembly cache and requires a signature from its publisher.</span></span> <span data-ttu-id="44a60-124">Os assemblies que não têm nome forte devem ser instalados no diretório do aplicativo do cliente.</span><span class="sxs-lookup"><span data-stu-id="44a60-124">Assemblies that are not strong named must be installed in the application directory of the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44a60-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44a60-125">See Also</span></span>  
 [<span data-ttu-id="44a60-126">Interoperação com código não gerenciado</span><span class="sxs-lookup"><span data-stu-id="44a60-126">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)  
 [<span data-ttu-id="44a60-127">Amostra de interoperabilidade COM: cliente COM e servidor .NET</span><span class="sxs-lookup"><span data-stu-id="44a60-127">COM Interop Sample: COM Client and .NET Server</span></span>](../../../docs/framework/interop/com-interop-sample-com-client-and-net-server.md)
