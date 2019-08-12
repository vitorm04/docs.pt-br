---
title: Tipos .NET qualificados para interoperação COM
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, qualifying .NET types
- qualifying .NET types for interoperation
- interoperation with unmanaged code, qualifying .NET types
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: 4b8afb52-fb8d-4e65-b47c-fd82956a3cdd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04ebdf5d3e5caf2c34823528703f75cf972f302f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631390"
---
# <a name="qualifying-net-types-for-com-interoperation"></a><span data-ttu-id="6f849-102">Tipos .NET qualificados para interoperação COM</span><span class="sxs-lookup"><span data-stu-id="6f849-102">Qualifying .NET Types for COM Interoperation</span></span>
<span data-ttu-id="6f849-103">Se você pretende expor os tipos em um assembly para aplicativos COM, considere os requisitos de interoperabilidade COM em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="6f849-103">If you intend to expose types in an assembly to COM applications, consider the requirements of COM interop at design time.</span></span> <span data-ttu-id="6f849-104">Tipos gerenciados (classe, interface, estrutura e enumeração) se integram perfeitamente com tipos COM quando você obedece às seguintes diretrizes:</span><span class="sxs-lookup"><span data-stu-id="6f849-104">Managed types (class, interface, structure, and enumeration) seamlessly integrate with COM types when you adhere to the following guidelines:</span></span>  
  
- <span data-ttu-id="6f849-105">As classes devem implementar interfaces explicitamente.</span><span class="sxs-lookup"><span data-stu-id="6f849-105">Classes should implement interfaces explicitly.</span></span>  
  
     <span data-ttu-id="6f849-106">Embora a interoperabilidade COM forneça um mecanismo para gerar automaticamente uma interface contendo todos os membros da classe e os membros da respectiva classe base, é muito melhor fornecer interfaces explícitas.</span><span class="sxs-lookup"><span data-stu-id="6f849-106">Although COM interop provides a mechanism to automatically generate an interface containing all members of the class and the members of its base class, it is far better to provide explicit interfaces.</span></span> <span data-ttu-id="6f849-107">A interface gerada automaticamente é chamada de interface de classe.</span><span class="sxs-lookup"><span data-stu-id="6f849-107">The automatically generated interface is called the class interface.</span></span> <span data-ttu-id="6f849-108">Para obter diretrizes, confira [Apresentando a interface de classe](com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="6f849-108">For guidelines, see [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
     <span data-ttu-id="6f849-109">Você pode usar Visual Basic, C# e C++ para incorporar as definições de interface no código, em vez de usar a linguagem IDL ou uma equivalente.</span><span class="sxs-lookup"><span data-stu-id="6f849-109">You can use Visual Basic, C#, and C++ to incorporate interface definitions in your code, instead of having to use Interface Definition Language (IDL) or its equivalent.</span></span> <span data-ttu-id="6f849-110">Para obter detalhes da sintaxe, consulte a documentação da linguagem.</span><span class="sxs-lookup"><span data-stu-id="6f849-110">For syntax details, see your language documentation.</span></span>  
  
- <span data-ttu-id="6f849-111">Os tipos gerenciados devem ser públicos.</span><span class="sxs-lookup"><span data-stu-id="6f849-111">Managed types must be public.</span></span>  
  
     <span data-ttu-id="6f849-112">Somente os tipos públicos em um assembly são registrados e exportados para a biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="6f849-112">Only public types in an assembly are registered and exported to the type library.</span></span> <span data-ttu-id="6f849-113">Como resultado, somente os tipos públicos são visíveis para COM.</span><span class="sxs-lookup"><span data-stu-id="6f849-113">As a result, only public types are visible to COM.</span></span>  
  
     <span data-ttu-id="6f849-114">Tipos gerenciados expõem recursos para outro código gerenciado que pode não ser exposto a COM.</span><span class="sxs-lookup"><span data-stu-id="6f849-114">Managed types expose features to other managed code that might not be exposed to COM.</span></span> <span data-ttu-id="6f849-115">Por exemplo, campos de constantes, construtores com parâmetros e métodos estáticos não são expostos a clientes COM.</span><span class="sxs-lookup"><span data-stu-id="6f849-115">For instance, parameterized constructors, static methods, and constant fields are not exposed to COM clients.</span></span> <span data-ttu-id="6f849-116">Além disso, como o tempo de execução realiza marshaling de dados dentro e fora de um tipo, os dados podem ser copiados ou transformados.</span><span class="sxs-lookup"><span data-stu-id="6f849-116">Further, as the runtime marshals data in and out of a type, the data might be copied or transformed.</span></span>  
  
- <span data-ttu-id="6f849-117">Propriedades, métodos, campos e eventos devem ser públicos.</span><span class="sxs-lookup"><span data-stu-id="6f849-117">Methods, properties, fields, and events must be public.</span></span>  
  
     <span data-ttu-id="6f849-118">Membros de tipos públicos também devem ser públicos para ser visíveis para COM.</span><span class="sxs-lookup"><span data-stu-id="6f849-118">Members of public types must also be public if they are to be visible to COM.</span></span> <span data-ttu-id="6f849-119">Você pode restringir a visibilidade de um assembly, um tipo público ou membros públicos de um tipo público aplicando o <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span><span class="sxs-lookup"><span data-stu-id="6f849-119">You can restrict the visibility of an assembly, a public type, or public members of a public type by applying the <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span></span> <span data-ttu-id="6f849-120">Por padrão, todos os membros e tipos públicos são visíveis.</span><span class="sxs-lookup"><span data-stu-id="6f849-120">By default, all public types and members are visible.</span></span>  
  
- <span data-ttu-id="6f849-121">Os tipos devem ter um construtor sem parâmetros público para ser ativado no COM.</span><span class="sxs-lookup"><span data-stu-id="6f849-121">Types must have a public parameterless constructor to be activated from COM.</span></span>  
  
     <span data-ttu-id="6f849-122">Tipos públicos gerenciados são visíveis para o COM.</span><span class="sxs-lookup"><span data-stu-id="6f849-122">Managed, public types are visible to COM.</span></span> <span data-ttu-id="6f849-123">No entanto, sem um construtor sem parâmetros público (um construtor sem argumentos), clientes COM não podem criar o tipo.</span><span class="sxs-lookup"><span data-stu-id="6f849-123">However, without a public parameterless constructor (a constructor with no arguments), COM clients cannot create the type.</span></span> <span data-ttu-id="6f849-124">Clientes COM ainda podem usar o tipo se ele é ativado por outros meios.</span><span class="sxs-lookup"><span data-stu-id="6f849-124">COM clients can still use the type if it is activated by some other means.</span></span>  
  
- <span data-ttu-id="6f849-125">Os tipos não podem ser abstratos.</span><span class="sxs-lookup"><span data-stu-id="6f849-125">Types cannot be abstract.</span></span>  
  
     <span data-ttu-id="6f849-126">Nem clientes COM, tampouco clientes .NET podem criar tipos abstratos.</span><span class="sxs-lookup"><span data-stu-id="6f849-126">Neither COM clients nor .NET clients can create abstract types.</span></span>  
  
 <span data-ttu-id="6f849-127">Quando exportados para COM, a hierarquia de herança de um tipo gerenciado é nivelada.</span><span class="sxs-lookup"><span data-stu-id="6f849-127">When exported to COM, the inheritance hierarchy of a managed type is flattened.</span></span> <span data-ttu-id="6f849-128">O controle de versão também difere entre ambientes gerenciados e não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="6f849-128">Versioning also differs between managed and unmanaged environments.</span></span> <span data-ttu-id="6f849-129">Os tipos expostos ao COM não têm as mesmas características de controle de versão de outros tipos gerenciados.</span><span class="sxs-lookup"><span data-stu-id="6f849-129">Types exposed to COM do not have the same versioning characteristics as other managed types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f849-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f849-130">See also</span></span>

- <xref:System.Runtime.InteropServices.ComVisibleAttribute>
- [<span data-ttu-id="6f849-131">Expondo componentes do .NET Framework ao COM</span><span class="sxs-lookup"><span data-stu-id="6f849-131">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="6f849-132">Apresentando a interface de classe</span><span class="sxs-lookup"><span data-stu-id="6f849-132">Introducing the class interface</span></span>](com-callable-wrapper.md#introducing-the-class-interface)
- [<span data-ttu-id="6f849-133">Aplicando atributos de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="6f849-133">Applying Interop Attributes</span></span>](../../../docs/standard/native-interop/apply-interop-attributes.md)
- [<span data-ttu-id="6f849-134">Como empacotar um assembly .NET Framework para o COM</span><span class="sxs-lookup"><span data-stu-id="6f849-134">Packaging a .NET Framework Assembly for COM</span></span>](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
