---
title: Tipos .NET qualificados para interoperação COM
description: Este artigo fornece diretrizes para ajudá-lo a expor tipos em um assembly .NET para aplicativos COM para interoperabilidade COM.
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, qualifying .NET types
- qualifying .NET types for interoperation
- interoperation with unmanaged code, qualifying .NET types
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: 4b8afb52-fb8d-4e65-b47c-fd82956a3cdd
ms.openlocfilehash: 5e8d604c8152d37475bf93e3b5687f24cfebfa02
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84285957"
---
# <a name="qualifying-net-types-for-com-interoperation"></a><span data-ttu-id="49b10-103">Tipos .NET qualificados para interoperação COM</span><span class="sxs-lookup"><span data-stu-id="49b10-103">Qualifying .NET Types for COM Interoperation</span></span>
<span data-ttu-id="49b10-104">Se você pretende expor os tipos em um assembly para aplicativos COM, considere os requisitos de interoperabilidade COM em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="49b10-104">If you intend to expose types in an assembly to COM applications, consider the requirements of COM interop at design time.</span></span> <span data-ttu-id="49b10-105">Tipos gerenciados (classe, interface, estrutura e enumeração) se integram perfeitamente com tipos COM quando você obedece às seguintes diretrizes:</span><span class="sxs-lookup"><span data-stu-id="49b10-105">Managed types (class, interface, structure, and enumeration) seamlessly integrate with COM types when you adhere to the following guidelines:</span></span>  
  
- <span data-ttu-id="49b10-106">As classes devem implementar interfaces explicitamente.</span><span class="sxs-lookup"><span data-stu-id="49b10-106">Classes should implement interfaces explicitly.</span></span>  
  
     <span data-ttu-id="49b10-107">Embora a interoperabilidade COM forneça um mecanismo para gerar automaticamente uma interface contendo todos os membros da classe e os membros da respectiva classe base, é muito melhor fornecer interfaces explícitas.</span><span class="sxs-lookup"><span data-stu-id="49b10-107">Although COM interop provides a mechanism to automatically generate an interface containing all members of the class and the members of its base class, it is far better to provide explicit interfaces.</span></span> <span data-ttu-id="49b10-108">A interface gerada automaticamente é chamada de interface de classe.</span><span class="sxs-lookup"><span data-stu-id="49b10-108">The automatically generated interface is called the class interface.</span></span> <span data-ttu-id="49b10-109">Para obter diretrizes, consulte [introdução à interface de classe](com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="49b10-109">For guidelines, see [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
     <span data-ttu-id="49b10-110">Você pode usar Visual Basic, C# e C++ para incorporar as definições de interface no código, em vez de usar a linguagem IDL ou uma equivalente.</span><span class="sxs-lookup"><span data-stu-id="49b10-110">You can use Visual Basic, C#, and C++ to incorporate interface definitions in your code, instead of having to use Interface Definition Language (IDL) or its equivalent.</span></span> <span data-ttu-id="49b10-111">Para obter detalhes da sintaxe, consulte a documentação da linguagem.</span><span class="sxs-lookup"><span data-stu-id="49b10-111">For syntax details, see your language documentation.</span></span>  
  
- <span data-ttu-id="49b10-112">Os tipos gerenciados devem ser públicos.</span><span class="sxs-lookup"><span data-stu-id="49b10-112">Managed types must be public.</span></span>  
  
     <span data-ttu-id="49b10-113">Somente os tipos públicos em um assembly são registrados e exportados para a biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="49b10-113">Only public types in an assembly are registered and exported to the type library.</span></span> <span data-ttu-id="49b10-114">Como resultado, somente os tipos públicos são visíveis para COM.</span><span class="sxs-lookup"><span data-stu-id="49b10-114">As a result, only public types are visible to COM.</span></span>  
  
     <span data-ttu-id="49b10-115">Tipos gerenciados expõem recursos para outro código gerenciado que pode não ser exposto a COM.</span><span class="sxs-lookup"><span data-stu-id="49b10-115">Managed types expose features to other managed code that might not be exposed to COM.</span></span> <span data-ttu-id="49b10-116">Por exemplo, campos de constantes, construtores com parâmetros e métodos estáticos não são expostos a clientes COM.</span><span class="sxs-lookup"><span data-stu-id="49b10-116">For instance, parameterized constructors, static methods, and constant fields are not exposed to COM clients.</span></span> <span data-ttu-id="49b10-117">Além disso, como o runtime realiza marshaling de dados dentro e fora de um tipo, os dados podem ser copiados ou transformados.</span><span class="sxs-lookup"><span data-stu-id="49b10-117">Further, as the runtime marshals data in and out of a type, the data might be copied or transformed.</span></span>  
  
- <span data-ttu-id="49b10-118">Propriedades, métodos, campos e eventos devem ser públicos.</span><span class="sxs-lookup"><span data-stu-id="49b10-118">Methods, properties, fields, and events must be public.</span></span>  
  
     <span data-ttu-id="49b10-119">Membros de tipos públicos também devem ser públicos para ser visíveis para COM.</span><span class="sxs-lookup"><span data-stu-id="49b10-119">Members of public types must also be public if they are to be visible to COM.</span></span> <span data-ttu-id="49b10-120">Você pode restringir a visibilidade de um assembly, um tipo público ou membros públicos de um tipo público aplicando o <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span><span class="sxs-lookup"><span data-stu-id="49b10-120">You can restrict the visibility of an assembly, a public type, or public members of a public type by applying the <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span></span> <span data-ttu-id="49b10-121">Por padrão, todos os membros e tipos públicos são visíveis.</span><span class="sxs-lookup"><span data-stu-id="49b10-121">By default, all public types and members are visible.</span></span>  
  
- <span data-ttu-id="49b10-122">Os tipos devem ter um construtor sem parâmetros público para ser ativado no COM.</span><span class="sxs-lookup"><span data-stu-id="49b10-122">Types must have a public parameterless constructor to be activated from COM.</span></span>  
  
     <span data-ttu-id="49b10-123">Tipos públicos gerenciados são visíveis para o COM.</span><span class="sxs-lookup"><span data-stu-id="49b10-123">Managed, public types are visible to COM.</span></span> <span data-ttu-id="49b10-124">No entanto, sem um construtor sem parâmetros público (um construtor sem argumentos), clientes COM não podem criar o tipo.</span><span class="sxs-lookup"><span data-stu-id="49b10-124">However, without a public parameterless constructor (a constructor with no arguments), COM clients cannot create the type.</span></span> <span data-ttu-id="49b10-125">Clientes COM ainda podem usar o tipo se ele é ativado por outros meios.</span><span class="sxs-lookup"><span data-stu-id="49b10-125">COM clients can still use the type if it is activated by some other means.</span></span>  
  
- <span data-ttu-id="49b10-126">Os tipos não podem ser abstratos.</span><span class="sxs-lookup"><span data-stu-id="49b10-126">Types cannot be abstract.</span></span>  
  
     <span data-ttu-id="49b10-127">Nem clientes COM, tampouco clientes .NET podem criar tipos abstratos.</span><span class="sxs-lookup"><span data-stu-id="49b10-127">Neither COM clients nor .NET clients can create abstract types.</span></span>  
  
 <span data-ttu-id="49b10-128">Quando exportados para COM, a hierarquia de herança de um tipo gerenciado é nivelada.</span><span class="sxs-lookup"><span data-stu-id="49b10-128">When exported to COM, the inheritance hierarchy of a managed type is flattened.</span></span> <span data-ttu-id="49b10-129">O controle de versão também difere entre ambientes gerenciados e não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="49b10-129">Versioning also differs between managed and unmanaged environments.</span></span> <span data-ttu-id="49b10-130">Os tipos expostos ao COM não têm as mesmas características de controle de versão de outros tipos gerenciados.</span><span class="sxs-lookup"><span data-stu-id="49b10-130">Types exposed to COM do not have the same versioning characteristics as other managed types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49b10-131">Veja também</span><span class="sxs-lookup"><span data-stu-id="49b10-131">See also</span></span>

- <xref:System.Runtime.InteropServices.ComVisibleAttribute>
- [<span data-ttu-id="49b10-132">Expondo componentes do .NET Framework para COM</span><span class="sxs-lookup"><span data-stu-id="49b10-132">Exposing .NET Framework Components to COM</span></span>](../../framework/interop/exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="49b10-133">Introdução à interface de classe</span><span class="sxs-lookup"><span data-stu-id="49b10-133">Introducing the class interface</span></span>](com-callable-wrapper.md#introducing-the-class-interface)
- [<span data-ttu-id="49b10-134">Aplicando atributos de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="49b10-134">Applying Interop Attributes</span></span>](apply-interop-attributes.md)
- [<span data-ttu-id="49b10-135">Como empacotar um assembly .NET Framework para o COM</span><span class="sxs-lookup"><span data-stu-id="49b10-135">Packaging a .NET Framework Assembly for COM</span></span>](../../framework/interop/packaging-an-assembly-for-com.md)
