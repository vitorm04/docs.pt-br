---
title: COM Callable Wrapper
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CCW
- COM interop, COM wrappers
- COM wrappers
- callable wrappers
- interoperation with unmanaged code, COM wrappers
- COM callable wrappers
ms.assetid: d04be3b5-27b9-4f5b-8469-a44149fabf78
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 270d7e85491f0f4ada797910d4fc12c1a14be625
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="com-callable-wrapper"></a><span data-ttu-id="8a06d-102">COM Callable Wrapper</span><span class="sxs-lookup"><span data-stu-id="8a06d-102">COM Callable Wrapper</span></span>
<span data-ttu-id="8a06d-103">Quando um cliente COM chama um objeto .NET, o Common Language Runtime cria o objeto gerenciado e um CCW (COM Callable Wrapper) para o objeto.</span><span class="sxs-lookup"><span data-stu-id="8a06d-103">When a COM client calls a .NET object, the common language runtime creates the managed object and a COM callable wrapper (CCW) for the object.</span></span> <span data-ttu-id="8a06d-104">Se não é possível referenciar um objeto .NET diretamente, os clientes COM usam o CCW como um proxy do objeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8a06d-104">Unable to reference a .NET object directly, COM clients use the CCW as a proxy for the managed object.</span></span>  
  
 <span data-ttu-id="8a06d-105">O tempo de execução cria exatamente um CCW para um objeto gerenciado, independentemente do número de clientes COM que solicita seus serviços.</span><span class="sxs-lookup"><span data-stu-id="8a06d-105">The runtime creates exactly one CCW for a managed object, regardless of the number of COM clients requesting its services.</span></span> <span data-ttu-id="8a06d-106">Como mostra a ilustração a seguir, vários clientes COM podem conter uma referência ao CCW que expõe a interface INew.</span><span class="sxs-lookup"><span data-stu-id="8a06d-106">As the following illustration shows, multiple COM clients can hold a reference to the CCW that exposes the INew interface.</span></span> <span data-ttu-id="8a06d-107">O CCW, por sua vez, contém uma única referência ao objeto gerenciado que implementa a interface e é coletada como lixo.</span><span class="sxs-lookup"><span data-stu-id="8a06d-107">The CCW, in turn, holds a single reference to the managed object that implements the interface and is garbage collected.</span></span> <span data-ttu-id="8a06d-108">Os clientes COM e .NET podem fazer solicitações no mesmo objeto gerenciado simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="8a06d-108">Both COM and .NET clients can make requests on the same managed object simultaneously.</span></span>  
  
 <span data-ttu-id="8a06d-109">![COM Callable Wrapper](./media/ccw.gif "ccw")</span><span class="sxs-lookup"><span data-stu-id="8a06d-109">![COM callable wrapper](./media/ccw.gif "ccw")</span></span>  
<span data-ttu-id="8a06d-110">Acessando objetos .NET por meio do COM Callable Wrapper</span><span class="sxs-lookup"><span data-stu-id="8a06d-110">Accessing .NET objects through COM callable wrapper</span></span>  
  
 <span data-ttu-id="8a06d-111">COM Callable Wrappers são invisíveis para outras classes em execução no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8a06d-111">COM callable wrappers are invisible to other classes running within the .NET Framework.</span></span> <span data-ttu-id="8a06d-112">Sua finalidade principal é realizar marshaling de chamadas entre o código gerenciado e não gerenciado; no entanto, os CCWs também gerenciam a identidade e o tempo de vida dos objetos gerenciados encapsulados por eles.</span><span class="sxs-lookup"><span data-stu-id="8a06d-112">Their primary purpose is to marshal calls between managed and unmanaged code; however, CCWs also manage the object identity and object lifetime of the managed objects they wrap.</span></span>  
  
## <a name="object-identity"></a><span data-ttu-id="8a06d-113">Identidade do objeto</span><span class="sxs-lookup"><span data-stu-id="8a06d-113">Object Identity</span></span>  
 <span data-ttu-id="8a06d-114">O tempo de execução aloca memória para o objeto .NET em seu heap coletado como lixo, que permite ao tempo de execução mover o objeto na memória, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="8a06d-114">The runtime allocates memory for the .NET object from its garbage-collected heap, which enables the runtime to move the object around in memory as necessary.</span></span> <span data-ttu-id="8a06d-115">Por outro lado, o tempo de execução aloca memória para o CCW em um heap não coletado, possibilitando que os clientes COM referenciem o wrapper diretamente.</span><span class="sxs-lookup"><span data-stu-id="8a06d-115">In contrast, the runtime allocates memory for the CCW from a noncollected heap, making it possible for COM clients to reference the wrapper directly.</span></span>  
  
## <a name="object-lifetime"></a><span data-ttu-id="8a06d-116">Tempo de vida do objeto</span><span class="sxs-lookup"><span data-stu-id="8a06d-116">Object Lifetime</span></span>  
 <span data-ttu-id="8a06d-117">Ao contrário do cliente .NET encapsulado por ele, o CCW é contado por referência no modo tradicional do COM.</span><span class="sxs-lookup"><span data-stu-id="8a06d-117">Unlike the .NET client it wraps, the CCW is reference-counted in traditional COM fashion.</span></span> <span data-ttu-id="8a06d-118">Quando a contagem de referência do CCW chega a zero, o wrapper libera sua referência no objeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8a06d-118">When the reference count on the CCW reaches zero, the wrapper releases its reference on the managed object.</span></span> <span data-ttu-id="8a06d-119">Um objeto gerenciado sem referências restantes é coletado durante o próximo ciclo de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="8a06d-119">A managed object with no remaining references is collected during the next garbage-collection cycle.</span></span>  
  
## <a name="simulating-com-interfaces"></a><span data-ttu-id="8a06d-120">Simulando Interfaces COM</span><span class="sxs-lookup"><span data-stu-id="8a06d-120">Simulating COM interfaces</span></span>

<span data-ttu-id="8a06d-121">CCW expõe todos os públicos, interfaces COM visíveis, tipos de dados e valores de retorno para clientes COM de uma maneira consistente com a imposição do COM de interação baseada em interface.</span><span class="sxs-lookup"><span data-stu-id="8a06d-121">CCW exposes all public, COM-visible interfaces, data types, and return values to COM clients in a manner that is consistent with COM's enforcement of interface-based interaction.</span></span> <span data-ttu-id="8a06d-122">Para um cliente COM, a invocação de métodos em um objeto .NET Framework é idêntica à invocação de métodos em um objeto COM.</span><span class="sxs-lookup"><span data-stu-id="8a06d-122">For a COM client, invoking methods on a .NET Framework object is identical to invoking methods on a COM object.</span></span>  
  
 <span data-ttu-id="8a06d-123">Para criar essa abordagem direta, o CCW fabrica interfaces COM tradicionais, como **IUnknown** e **IDispatch**.</span><span class="sxs-lookup"><span data-stu-id="8a06d-123">To create this seamless approach, the CCW manufactures traditional COM interfaces, such as **IUnknown** and **IDispatch**.</span></span> <span data-ttu-id="8a06d-124">Como mostra a ilustração a seguir, o CCW mantém uma única referência no objeto .NET encapsulado por ele.</span><span class="sxs-lookup"><span data-stu-id="8a06d-124">As the following illustration shows, the CCW maintains a single reference on the .NET object that it wraps.</span></span> <span data-ttu-id="8a06d-125">O cliente COM e o objeto .NET interagem mutuamente por meio do proxy e da construção de stub do CCW.</span><span class="sxs-lookup"><span data-stu-id="8a06d-125">Both the COM client and .NET object interact with each other through the proxy and stub construction of the CCW.</span></span>  
  
 <span data-ttu-id="8a06d-126">![Interfaces COM](./media/ccwwithinterfaces.gif "ccwwithinterfaces")</span><span class="sxs-lookup"><span data-stu-id="8a06d-126">![COM interfaces](./media/ccwwithinterfaces.gif "ccwwithinterfaces")</span></span>  
<span data-ttu-id="8a06d-127">Interfaces COM e COM callable wrapper</span><span class="sxs-lookup"><span data-stu-id="8a06d-127">COM interfaces and the COM callable wrapper</span></span>  
  
 <span data-ttu-id="8a06d-128">Além de expor as interfaces que são implementadas explicitamente por uma classe no ambiente gerenciado, o .NET Framework fornece implementações das interfaces COM listadas na tabela a seguir em nome do objeto.</span><span class="sxs-lookup"><span data-stu-id="8a06d-128">In addition to exposing the interfaces that are explicitly implemented by a class in the managed environment, the .NET Framework supplies implementations of the COM interfaces listed in the following table on behalf of the object.</span></span> <span data-ttu-id="8a06d-129">Uma classe .NET pode substituir o comportamento padrão fornecendo sua própria implementação dessas interfaces.</span><span class="sxs-lookup"><span data-stu-id="8a06d-129">A .NET class can override the default behavior by providing its own implementation of these interfaces.</span></span> <span data-ttu-id="8a06d-130">No entanto, o tempo de execução sempre fornece a implementação para as interfaces **IUnknown** e **IDispatch**.</span><span class="sxs-lookup"><span data-stu-id="8a06d-130">However, the runtime always provides the implementation for the **IUnknown** and **IDispatch** interfaces.</span></span>  
  
|<span data-ttu-id="8a06d-131">Interface</span><span class="sxs-lookup"><span data-stu-id="8a06d-131">Interface</span></span>|<span data-ttu-id="8a06d-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a06d-132">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8a06d-133">**Idispatch**</span><span class="sxs-lookup"><span data-stu-id="8a06d-133">**Idispatch**</span></span>|<span data-ttu-id="8a06d-134">Fornece um mecanismo de associação tardia ao tipo.</span><span class="sxs-lookup"><span data-stu-id="8a06d-134">Provides a mechanism for late binding to type.</span></span>|  
|<span data-ttu-id="8a06d-135">**IerrorInfo**</span><span class="sxs-lookup"><span data-stu-id="8a06d-135">**IerrorInfo**</span></span>|<span data-ttu-id="8a06d-136">Fornece uma descrição textual do erro, sua origem, um arquivo de Ajuda, um contexto de Ajuda e o GUID da interface que definiu o erro (sempre **GUID_NULL** para classes do .NET).</span><span class="sxs-lookup"><span data-stu-id="8a06d-136">Provides a textual description of the error, its source, a Help file, Help context, and the GUID of the interface that defined the error (always **GUID_NULL** for .NET classes).</span></span>|  
|<span data-ttu-id="8a06d-137">**IprovideClassInfo**</span><span class="sxs-lookup"><span data-stu-id="8a06d-137">**IprovideClassInfo**</span></span>|<span data-ttu-id="8a06d-138">Permite aos clientes COM obter acesso à interface **ITypeInfo** implementada por uma classe gerenciada.</span><span class="sxs-lookup"><span data-stu-id="8a06d-138">Enables COM clients to gain access to the **ITypeInfo** interface implemented by a managed class.</span></span>|  
|<span data-ttu-id="8a06d-139">**IsupportErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="8a06d-139">**IsupportErrorInfo**</span></span>|<span data-ttu-id="8a06d-140">Permite a um cliente COM determinar se o objeto gerenciado dá suporte à interface **IErrorInfo**.</span><span class="sxs-lookup"><span data-stu-id="8a06d-140">Enables a COM client to determine whether the managed object supports the **IErrorInfo** interface.</span></span> <span data-ttu-id="8a06d-141">Nesse caso, permite ao cliente obter um ponteiro para o último objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="8a06d-141">If so, enables the client to obtain a pointer to the latest exception object.</span></span> <span data-ttu-id="8a06d-142">Todos os tipos gerenciados dão suporte à interface **IErrorInfo**.</span><span class="sxs-lookup"><span data-stu-id="8a06d-142">All managed types support the **IErrorInfo** interface.</span></span>|  
|<span data-ttu-id="8a06d-143">**ItypeInfo**</span><span class="sxs-lookup"><span data-stu-id="8a06d-143">**ItypeInfo**</span></span>|<span data-ttu-id="8a06d-144">Fornece informações de tipo de uma classe que são exatamente iguais às informações de tipo produzidas pelo Tlbexp.exe.</span><span class="sxs-lookup"><span data-stu-id="8a06d-144">Provides type information for a class that is exactly the same as the type information produced by Tlbexp.exe.</span></span>|  
|<span data-ttu-id="8a06d-145">**Iunknown**</span><span class="sxs-lookup"><span data-stu-id="8a06d-145">**Iunknown**</span></span>|<span data-ttu-id="8a06d-146">Fornece a implementação padrão da interface **IUnknown** com a qual o cliente COM gerencia o tempo de vida do CCW e fornece a coerção de tipo.</span><span class="sxs-lookup"><span data-stu-id="8a06d-146">Provides the standard implementation of the **IUnknown** interface with which the COM client manages the lifetime of the CCW and provides type coercion.</span></span>|  
  
 <span data-ttu-id="8a06d-147">Uma classe gerenciada também pode fornecer as interfaces COM descritas na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="8a06d-147">A managed class can also provide the COM interfaces described in the following table.</span></span>  
  
|<span data-ttu-id="8a06d-148">Interface</span><span class="sxs-lookup"><span data-stu-id="8a06d-148">Interface</span></span>|<span data-ttu-id="8a06d-149">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a06d-149">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8a06d-150">A (\_*classname*) interface de classe</span><span class="sxs-lookup"><span data-stu-id="8a06d-150">The (\_*classname*) class interface</span></span>|<span data-ttu-id="8a06d-151">Interface, exposta pelo tempo de execução e não definida explicitamente, que expõe todas as interfaces públicas, métodos, propriedades e campos que são expostos explicitamente em um objeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8a06d-151">Interface, exposed by the runtime and not explicitly defined, that exposes all public interfaces, methods, properties, and fields that are explicitly exposed on a managed object.</span></span>|  
|<span data-ttu-id="8a06d-152">**IConnectionPoint** e **IconnectionPointContainer**</span><span class="sxs-lookup"><span data-stu-id="8a06d-152">**IConnectionPoint** and **IconnectionPointContainer**</span></span>|<span data-ttu-id="8a06d-153">Interface para objetos que dão origem a eventos baseados em representante (uma interface para o registro de assinantes do evento).</span><span class="sxs-lookup"><span data-stu-id="8a06d-153">Interface for objects that source delegate-based events (an interface for registering event subscribers).</span></span>|  
|<span data-ttu-id="8a06d-154">**IdispatchEx**</span><span class="sxs-lookup"><span data-stu-id="8a06d-154">**IdispatchEx**</span></span>|<span data-ttu-id="8a06d-155">Interface fornecida pelo tempo de execução se a classe implementa **IExpando**.</span><span class="sxs-lookup"><span data-stu-id="8a06d-155">Interface supplied by the runtime if the class implements **IExpando**.</span></span> <span data-ttu-id="8a06d-156">A interface **IDispatchEx** é uma extensão da interface **IDispatch** que, ao contrário de **IDispatch**, permite a enumeração, adição, exclusão e chamada de membros que diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="8a06d-156">The **IDispatchEx** interface is an extension of the **IDispatch** interface that, unlike **IDispatch**, enables enumeration, addition, deletion, and case-sensitive calling of members.</span></span>|  
|<span data-ttu-id="8a06d-157">**IEnumVARIANT**</span><span class="sxs-lookup"><span data-stu-id="8a06d-157">**IEnumVARIANT**</span></span>|<span data-ttu-id="8a06d-158">Interface para classes de tipo de coleção, que enumera os objetos na coleção, se a classe implementa **IEnumerable**.</span><span class="sxs-lookup"><span data-stu-id="8a06d-158">Interface for collection-type classes, which enumerates the objects in the collection if the class implements **IEnumerable**.</span></span>|  
  
## <a name="introducing-the-class-interface"></a><span data-ttu-id="8a06d-159">Introdução à interface de classe</span><span class="sxs-lookup"><span data-stu-id="8a06d-159">Introducing the class interface</span></span>  
 <span data-ttu-id="8a06d-160">A interface de classe, que não é definida explicitamente no código gerenciado, é uma interface que expõe todos os métodos públicos, propriedades, campos e eventos que são expostos explicitamente no objeto .NET.</span><span class="sxs-lookup"><span data-stu-id="8a06d-160">The class interface, which is not explicitly defined in managed code, is an interface that exposes all public methods, properties, fields, and events that are explicitly exposed on the .NET object.</span></span> <span data-ttu-id="8a06d-161">Essa interface pode ser uma interface dupla ou somente de expedição.</span><span class="sxs-lookup"><span data-stu-id="8a06d-161">This interface can be a dual or dispatch-only interface.</span></span> <span data-ttu-id="8a06d-162">A interface de classe recebe o nome da própria classe do .NET, precedido por um sublinhado.</span><span class="sxs-lookup"><span data-stu-id="8a06d-162">The class interface receives the name of the .NET class itself, preceded by an underscore.</span></span> <span data-ttu-id="8a06d-163">Por exemplo, para a classe mamífero, a interface de classe é \_mamífero.</span><span class="sxs-lookup"><span data-stu-id="8a06d-163">For example, for class Mammal, the class interface is \_Mammal.</span></span>  
  
 <span data-ttu-id="8a06d-164">Para classes derivadas, a interface de classe também expõe todos os métodos públicos, propriedades e campos da classe base.</span><span class="sxs-lookup"><span data-stu-id="8a06d-164">For derived classes, the class interface also exposes all public methods, properties, and fields of the base class.</span></span> <span data-ttu-id="8a06d-165">A classe derivada também expõe uma interface de classe para cada classe base.</span><span class="sxs-lookup"><span data-stu-id="8a06d-165">The derived class also exposes a class interface for each base class.</span></span> <span data-ttu-id="8a06d-166">Por exemplo, se a classe mamífero estende a classe MammalSuperclass, que por si só estende System. Object, o expõe de objeto do .NET para clientes COM três interfaces de chamada de classe \_mamífero, \_MammalSuperclass, e \_objeto.</span><span class="sxs-lookup"><span data-stu-id="8a06d-166">For example, if class Mammal extends class MammalSuperclass, which itself extends System.Object, the .NET object exposes to COM clients three class interfaces named \_Mammal, \_MammalSuperclass, and \_Object.</span></span>  
  
 <span data-ttu-id="8a06d-167">Por exemplo, considere a seguinte classe do .NET:</span><span class="sxs-lookup"><span data-stu-id="8a06d-167">For example, consider the following .NET class:</span></span>  
  
```vb  
' Applies the ClassInterfaceAttribute to set the interface to dual.  
<ClassInterface(ClassInterfaceType.AutoDual)> _  
' Implicitly extends System.Object.  
Public Class Mammal  
    Sub Eat()  
    Sub Breathe()  
    Sub Sleep()  
End Class  
```  
  
```csharp  
// Applies the ClassInterfaceAttribute to set the interface to dual.  
[ClassInterface(ClassInterfaceType.AutoDual)]  
// Implicitly extends System.Object.  
public class Mammal  
{  
    void  Eat();  
    void  Breathe():  
    void  Sleep();  
}  
```  
  
 <span data-ttu-id="8a06d-168">O cliente COM pode obter um ponteiro para uma interface de classe chamado `_Mammal`, que é descrito na biblioteca de tipos gerada pela ferramenta [Exportador da Biblioteca de Tipos (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="8a06d-168">The COM client can obtain a pointer to a class interface named `_Mammal`, which is described in the type library that the [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) tool generates.</span></span> <span data-ttu-id="8a06d-169">Se a classe `Mammal` tiver implementado uma ou mais interfaces, as interfaces aparecerão na coclass.</span><span class="sxs-lookup"><span data-stu-id="8a06d-169">If the `Mammal` class implemented one or more interfaces, the interfaces would appear under the coclass.</span></span>  
  
```  
[odl, uuid(…), hidden, dual, nonextensible, oleautomation]  
interface _Mammal : IDispatch  
{  
    [id(0x00000000), propget] HRESULT ToString([out, retval] BSTR*  
        pRetVal);  
    [id(0x60020001)] HRESULT Equals([in] VARIANT obj, [out, retval]  
        VARIANT_BOOL* pRetVal);  
    [id(0x60020002)] HRESULT GetHashCode([out, retval] short* pRetVal);  
    [id(0x60020003)] HRESULT GetType([out, retval] _Type** pRetVal);  
    [id(0x6002000d)] HRESULT Eat();  
    [id(0x6002000e)] HRESULT Breathe();  
    [id(0x6002000f)] HRESULT Sleep();  
}  
[uuid(…)]  
coclass Mammal   
{  
    [default] interface _Mammal;  
}  
```  
  
 <span data-ttu-id="8a06d-170">A geração da interface de classe é opcional.</span><span class="sxs-lookup"><span data-stu-id="8a06d-170">Generating the class interface is optional.</span></span> <span data-ttu-id="8a06d-171">Por padrão, a interoperabilidade COM gera uma interface somente de expedição para cada classe exportada para uma biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="8a06d-171">By default, COM interop generates a dispatch-only interface for each class you export to a type library.</span></span> <span data-ttu-id="8a06d-172">É possível impedir ou modificar a criação automática dessa interface aplicando o <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> à classe.</span><span class="sxs-lookup"><span data-stu-id="8a06d-172">You can prevent or modify the automatic creation of this interface by applying the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> to your class.</span></span> <span data-ttu-id="8a06d-173">Embora a interface de classe possa facilitar a tarefa de exposição das classes gerenciadas ao COM, seus usos são limitados.</span><span class="sxs-lookup"><span data-stu-id="8a06d-173">Although the class interface can ease the task of exposing managed classes to COM, its uses are limited.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="8a06d-174">O uso da interface de classe, em vez da definição explícita de sua própria, pode complicar o controle futuro de versão da classe gerenciada.</span><span class="sxs-lookup"><span data-stu-id="8a06d-174">Using the class interface, instead of explicitly defining your own, can complicate the future versioning of your managed class.</span></span> <span data-ttu-id="8a06d-175">Leia as diretrizes a seguir antes de usar a interface de classe.</span><span class="sxs-lookup"><span data-stu-id="8a06d-175">Please read the following guidelines before using the class interface.</span></span>  
  
### <a name="define-an-explicit-interface-for-com-clients-to-use-rather-than-generating-the-class-interface"></a><span data-ttu-id="8a06d-176">Defina uma interface explícita para uso dos clientes COM, em vez de gerar a interface de classe.</span><span class="sxs-lookup"><span data-stu-id="8a06d-176">Define an explicit interface for COM clients to use rather than generating the class interface.</span></span>  
 <span data-ttu-id="8a06d-177">Como a interoperabilidade COM gera uma interface de classe automaticamente, alterações posteriores à versão na classe podem alterar o layout da interface de classe exposta pelo Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="8a06d-177">Because COM interop generates a class interface automatically, post-version changes to your class can alter the layout of the class interface exposed by the common language runtime.</span></span> <span data-ttu-id="8a06d-178">Já que os clientes COM não estão normalmente preparados para manipular as alterações no layout de uma interface, eles são interrompidos se o layout de membro da classe é alterado.</span><span class="sxs-lookup"><span data-stu-id="8a06d-178">Since COM clients are typically unprepared to handle changes in the layout of an interface, they break if you change the member layout of the class.</span></span>  
  
 <span data-ttu-id="8a06d-179">Esta diretriz reforça a noção de que as interfaces expostas para os clientes COM devem permanecer inalteráveis.</span><span class="sxs-lookup"><span data-stu-id="8a06d-179">This guideline reinforces the notion that interfaces exposed to COM clients must remain unchangeable.</span></span> <span data-ttu-id="8a06d-180">Para reduzir o risco de interromper os clientes COM reordenando inadvertidamente o layout da interface, isole todas as alterações na classe do layout da interface definindo interfaces explicitamente.</span><span class="sxs-lookup"><span data-stu-id="8a06d-180">To reduce the risk of breaking COM clients by inadvertently reordering the interface layout, isolate all changes to the class from the interface layout by explicitly defining interfaces.</span></span>  
  
 <span data-ttu-id="8a06d-181">Use o **ClassInterfaceAttribute** para desativar a geração automática da interface de classe e implementar uma interface explícita para a classe, como mostra o seguinte fragmento de código:</span><span class="sxs-lookup"><span data-stu-id="8a06d-181">Use the **ClassInterfaceAttribute** to disengage the automatic generation of the class interface and implement an explicit interface for the class, as the following code fragment shows:</span></span>  
  
```vb  
<ClassInterface(ClassInterfaceType.None)>Public Class LoanApp  
    Implements IExplicit  
    Sub M() Implements IExplicit.M  
…  
End Class  
```  
  
```csharp  
[ClassInterface(ClassInterfaceType.None)]  
public class LoanApp : IExplicit {  
    void M();  
}  
```  
  
 <span data-ttu-id="8a06d-182">O valor **ClassInterfaceType.None** impede que a interface de classe seja gerada quando os metadados da classe são exportados para uma biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="8a06d-182">The **ClassInterfaceType.None** value prevents the class interface from being generated when the class metadata is exported to a type library.</span></span> <span data-ttu-id="8a06d-183">No exemplo anterior, os clientes COM podem acessar a classe `LoanApp` somente pela interface `IExplicit`.</span><span class="sxs-lookup"><span data-stu-id="8a06d-183">In the preceding example, COM clients can access the `LoanApp` class only through the `IExplicit` interface.</span></span>  
  
### <a name="avoid-caching-dispatch-identifiers-dispids"></a><span data-ttu-id="8a06d-184">Evitar o cache de identificadores de despacho (DispIds)</span><span class="sxs-lookup"><span data-stu-id="8a06d-184">Avoid caching dispatch identifiers (DispIds)</span></span>
 <span data-ttu-id="8a06d-185">O uso da interface de classe é uma opção aceitável para os clientes com script, os clientes do Microsoft Visual Basic 6.0 ou qualquer cliente de associação tardia que não armazena em cache os DispIds dos membros da interface.</span><span class="sxs-lookup"><span data-stu-id="8a06d-185">Using the class interface is an acceptable option for scripted clients, Microsoft Visual Basic 6.0 clients, or any late-bound client that does not cache the DispIds of interface members.</span></span> <span data-ttu-id="8a06d-186">Os DispIds identificam os membros da interface para habilitar a associação tardia.</span><span class="sxs-lookup"><span data-stu-id="8a06d-186">DispIds identify interface members to enable late binding.</span></span>  
  
 <span data-ttu-id="8a06d-187">Para a interface de classe, a geração dos DispIds se baseia na posição do membro na interface.</span><span class="sxs-lookup"><span data-stu-id="8a06d-187">For the class interface, generation of DispIds is based on the position of the member in the interface.</span></span> <span data-ttu-id="8a06d-188">Se você alterar a ordem do membro e exportar a classe para uma biblioteca de tipos, você alterará os DispIds gerados na interface de classe.</span><span class="sxs-lookup"><span data-stu-id="8a06d-188">If you change the order of the member and export the class to a type library, you will alter the DispIds generated in the class interface.</span></span>  
  
 <span data-ttu-id="8a06d-189">Para evitar a interrupção de clientes COM de associação tardia ao usar a interface de classe, aplique o **ClassInterfaceAttribute** ao valor **ClassInterfaceType.AutoDispatch**.</span><span class="sxs-lookup"><span data-stu-id="8a06d-189">To avoid breaking late-bound COM clients when using the class interface, apply the **ClassInterfaceAttribute** with the **ClassInterfaceType.AutoDispatch** value.</span></span> <span data-ttu-id="8a06d-190">Esse valor implementa uma interface de classe somente de expedição, mas omite a descrição da interface na biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="8a06d-190">This value implements a dispatch-only class interface, but omits the interface description from the type library.</span></span> <span data-ttu-id="8a06d-191">Sem uma descrição da interface, os clientes não conseguem armazenar em cache os DispIds em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="8a06d-191">Without an interface description, clients are unable to cache DispIds at compile time.</span></span> <span data-ttu-id="8a06d-192">Embora esse seja o tipo de interface padrão para a interface de classe, é possível aplicar o valor do atributo explicitamente.</span><span class="sxs-lookup"><span data-stu-id="8a06d-192">Although this is the default interface type for the class interface, you can apply the attribute value explicitly.</span></span>  
  
```vb  
<ClassInterface(ClassInterfaceType.AutoDispatch)> Public Class LoanApp  
    Implements IAnother  
    Sub M() Implements IAnother.M  
…  
End Class  
```  
  
```csharp  
[ClassInterface(ClassInterfaceType.AutoDispatch]  
public class LoanApp : IAnother {  
    void M();  
}  
```  
  
 <span data-ttu-id="8a06d-193">Para obter o DispId de um membro da interface em tempo de execução, os clientes COM podem chamar **IDispatch.GetIdsOfNames**.</span><span class="sxs-lookup"><span data-stu-id="8a06d-193">To get the DispId of an interface member at run time, COM clients can call **IDispatch.GetIdsOfNames**.</span></span> <span data-ttu-id="8a06d-194">Para invocar um método na interface, passe o DispId retornado como um argumento para **IDispatch.Invoke**.</span><span class="sxs-lookup"><span data-stu-id="8a06d-194">To invoke a method on the interface, pass the returned DispId as an argument to **IDispatch.Invoke**.</span></span>  
  
### <a name="restrict-using-the-dual-interface-option-for-the-class-interface"></a><span data-ttu-id="8a06d-195">Restrinja o uso da opção de interface dupla para a interface de classe.</span><span class="sxs-lookup"><span data-stu-id="8a06d-195">Restrict using the dual interface option for the class interface.</span></span>  
 <span data-ttu-id="8a06d-196">Interfaces duplas permitem a associação inicial e tardia a membros da interface por clientes COM.</span><span class="sxs-lookup"><span data-stu-id="8a06d-196">Dual interfaces enable early and late binding to interface members by COM clients.</span></span> <span data-ttu-id="8a06d-197">Em tempo de design e durante o teste, talvez seja útil definir a interface de classe como dupla.</span><span class="sxs-lookup"><span data-stu-id="8a06d-197">At design time and during testing, you might find it useful to set the class interface to dual.</span></span> <span data-ttu-id="8a06d-198">Para uma classe gerenciada (e suas classes base) que nunca serão modificadas, essa opção também é aceitável.</span><span class="sxs-lookup"><span data-stu-id="8a06d-198">For a managed class (and its base classes) that will never be modified, this option is also acceptable.</span></span> <span data-ttu-id="8a06d-199">Em todos os outros casos, evite definir a interface de classe como dupla.</span><span class="sxs-lookup"><span data-stu-id="8a06d-199">In all other cases, avoid setting the class interface to dual.</span></span>  
  
 <span data-ttu-id="8a06d-200">Uma interface dupla gerada automaticamente pode ser apropriada em casos raros. No entanto, com mais frequência, ela cria complexidade relacionada à versão.</span><span class="sxs-lookup"><span data-stu-id="8a06d-200">An automatically generated dual interface might be appropriate in rare cases; however, more often it creates version-related complexity.</span></span> <span data-ttu-id="8a06d-201">Por exemplo, os clientes COM que usam a interface de classe de uma classe derivada podem ser facilmente interrompidos com alterações na classe base.</span><span class="sxs-lookup"><span data-stu-id="8a06d-201">For example, COM clients using the class interface of a derived class can easily break with changes to the base class.</span></span> <span data-ttu-id="8a06d-202">Quando um terceiro fornece a classe base, o layout da interface de classe fica fora de seu controle.</span><span class="sxs-lookup"><span data-stu-id="8a06d-202">When a third party provides the base class, the layout of the class interface is out of your control.</span></span> <span data-ttu-id="8a06d-203">Além disso, ao contrário de uma interface somente de expedição, uma interface dupla (**ClassInterface.AutoDual**) fornece uma descrição da interface de classe na biblioteca de tipos exportada.</span><span class="sxs-lookup"><span data-stu-id="8a06d-203">Further, unlike a dispatch-only interface, a dual interface (**ClassInterface.AutoDual**) provides a description of the class interface in the exported type library.</span></span> <span data-ttu-id="8a06d-204">Uma descrição como essa incentiva os clientes de associação tardia a armazenarem em cache os DispIds em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8a06d-204">Such a description encourages late-bound clients to cache DispIds at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a06d-205">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a06d-205">See Also</span></span>  
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>  
 [<span data-ttu-id="8a06d-206">Wrappers COM</span><span class="sxs-lookup"><span data-stu-id="8a06d-206">COM Wrappers</span></span>](com-wrappers.md)  
 [<span data-ttu-id="8a06d-207">Expondo componentes do .NET Framework ao COM</span><span class="sxs-lookup"><span data-stu-id="8a06d-207">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="8a06d-208">Qualificando tipos .NET para interoperação</span><span class="sxs-lookup"><span data-stu-id="8a06d-208">Qualifying .NET Types for Interoperation</span></span>](qualifying-net-types-for-interoperation.md)  
 [<span data-ttu-id="8a06d-209">RCW (Runtime Callable Wrapper)</span><span class="sxs-lookup"><span data-stu-id="8a06d-209">Runtime Callable Wrapper</span></span>](runtime-callable-wrapper.md)