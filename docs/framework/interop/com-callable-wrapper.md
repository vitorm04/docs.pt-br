---
title: COM Callable Wrapper
ms.date: 10/23/2018
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
ms.openlocfilehash: 942ba933126da291e072270318a5657953ddcdb8
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613246"
---
# <a name="com-callable-wrapper"></a><span data-ttu-id="62620-102">COM Callable Wrapper</span><span class="sxs-lookup"><span data-stu-id="62620-102">COM Callable Wrapper</span></span>

<span data-ttu-id="62620-103">Quando um cliente COM chama um objeto .NET, o Common Language Runtime cria o objeto gerenciado e um CCW (COM Callable Wrapper) para o objeto.</span><span class="sxs-lookup"><span data-stu-id="62620-103">When a COM client calls a .NET object, the common language runtime creates the managed object and a COM callable wrapper (CCW) for the object.</span></span> <span data-ttu-id="62620-104">Se não é possível referenciar um objeto .NET diretamente, os clientes COM usam o CCW como um proxy do objeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="62620-104">Unable to reference a .NET object directly, COM clients use the CCW as a proxy for the managed object.</span></span>

<span data-ttu-id="62620-105">O tempo de execução cria exatamente um CCW para um objeto gerenciado, independentemente do número de clientes COM que solicita seus serviços.</span><span class="sxs-lookup"><span data-stu-id="62620-105">The runtime creates exactly one CCW for a managed object, regardless of the number of COM clients requesting its services.</span></span> <span data-ttu-id="62620-106">Como mostra a ilustração a seguir, vários clientes COM podem conter uma referência ao CCW que expõe a interface INew.</span><span class="sxs-lookup"><span data-stu-id="62620-106">As the following illustration shows, multiple COM clients can hold a reference to the CCW that exposes the INew interface.</span></span> <span data-ttu-id="62620-107">O CCW, por sua vez, contém uma única referência ao objeto gerenciado que implementa a interface e é coletada como lixo.</span><span class="sxs-lookup"><span data-stu-id="62620-107">The CCW, in turn, holds a single reference to the managed object that implements the interface and is garbage collected.</span></span> <span data-ttu-id="62620-108">Os clientes COM e .NET podem fazer solicitações no mesmo objeto gerenciado simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="62620-108">Both COM and .NET clients can make requests on the same managed object simultaneously.</span></span>

![Vários clientes COM que contêm uma referência ao CCW que expõe INew.](./media/com-callable-wrapper/com-callable-wrapper-clients.gif)

<span data-ttu-id="62620-110">COM Callable Wrappers são invisíveis para outras classes em execução no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="62620-110">COM callable wrappers are invisible to other classes running within the .NET Framework.</span></span> <span data-ttu-id="62620-111">Sua finalidade principal é realizar marshaling de chamadas entre o código gerenciado e não gerenciado; no entanto, os CCWs também gerenciam a identidade e o tempo de vida dos objetos gerenciados encapsulados por eles.</span><span class="sxs-lookup"><span data-stu-id="62620-111">Their primary purpose is to marshal calls between managed and unmanaged code; however, CCWs also manage the object identity and object lifetime of the managed objects they wrap.</span></span>

## <a name="object-identity"></a><span data-ttu-id="62620-112">Identidade do objeto</span><span class="sxs-lookup"><span data-stu-id="62620-112">Object Identity</span></span>

<span data-ttu-id="62620-113">O tempo de execução aloca memória para o objeto .NET em seu heap coletado como lixo, que permite ao tempo de execução mover o objeto na memória, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="62620-113">The runtime allocates memory for the .NET object from its garbage-collected heap, which enables the runtime to move the object around in memory as necessary.</span></span> <span data-ttu-id="62620-114">Por outro lado, o tempo de execução aloca memória para o CCW em um heap não coletado, possibilitando que os clientes COM referenciem o wrapper diretamente.</span><span class="sxs-lookup"><span data-stu-id="62620-114">In contrast, the runtime allocates memory for the CCW from a noncollected heap, making it possible for COM clients to reference the wrapper directly.</span></span>

## <a name="object-lifetime"></a><span data-ttu-id="62620-115">Tempo de vida do objeto</span><span class="sxs-lookup"><span data-stu-id="62620-115">Object Lifetime</span></span>

<span data-ttu-id="62620-116">Ao contrário do cliente .NET encapsulado por ele, o CCW é contado por referência no modo tradicional do COM.</span><span class="sxs-lookup"><span data-stu-id="62620-116">Unlike the .NET client it wraps, the CCW is reference-counted in traditional COM fashion.</span></span> <span data-ttu-id="62620-117">Quando a contagem de referência do CCW chega a zero, o wrapper libera sua referência no objeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="62620-117">When the reference count on the CCW reaches zero, the wrapper releases its reference on the managed object.</span></span> <span data-ttu-id="62620-118">Um objeto gerenciado sem referências restantes é coletado durante o próximo ciclo de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="62620-118">A managed object with no remaining references is collected during the next garbage-collection cycle.</span></span>

## <a name="simulating-com-interfaces"></a><span data-ttu-id="62620-119">Simulando Interfaces COM</span><span class="sxs-lookup"><span data-stu-id="62620-119">Simulating COM interfaces</span></span>

<span data-ttu-id="62620-120">O CCW expõe todas as interfaces públicas visíveis para o COM, os tipos de dados e os valores retornados para clientes COM de uma maneira consistente com a exigência do COM em relação à interação baseada em interface.</span><span class="sxs-lookup"><span data-stu-id="62620-120">CCW exposes all public, COM-visible interfaces, data types, and return values to COM clients in a manner that is consistent with COM's enforcement of interface-based interaction.</span></span> <span data-ttu-id="62620-121">Para um cliente COM, a invocação de métodos em um objeto .NET Framework é idêntica à invocação de métodos em um objeto COM.</span><span class="sxs-lookup"><span data-stu-id="62620-121">For a COM client, invoking methods on a .NET Framework object is identical to invoking methods on a COM object.</span></span>

<span data-ttu-id="62620-122">Para criar essa abordagem direta, o CCW fabrica interfaces COM tradicionais, como **IUnknown** e **IDispatch**.</span><span class="sxs-lookup"><span data-stu-id="62620-122">To create this seamless approach, the CCW manufactures traditional COM interfaces, such as **IUnknown** and **IDispatch**.</span></span> <span data-ttu-id="62620-123">Como mostra a ilustração a seguir, o CCW mantém uma única referência no objeto .NET encapsulado por ele.</span><span class="sxs-lookup"><span data-stu-id="62620-123">As the following illustration shows, the CCW maintains a single reference on the .NET object that it wraps.</span></span> <span data-ttu-id="62620-124">O cliente COM e o objeto .NET interagem mutuamente por meio do proxy e da construção de stub do CCW.</span><span class="sxs-lookup"><span data-stu-id="62620-124">Both the COM client and the .NET object interact with each other through the proxy and stub construction of the CCW.</span></span>

![Diagrama que mostra como a CCW fabrica interfaces COM.](./media/com-callable-wrapper/com-callable-wrapper-interfaces.gif)

<span data-ttu-id="62620-126">Além de expor as interfaces que são implementadas explicitamente por uma classe no ambiente gerenciado, o .NET Framework fornece implementações das interfaces COM listadas na tabela a seguir em nome do objeto.</span><span class="sxs-lookup"><span data-stu-id="62620-126">In addition to exposing the interfaces that are explicitly implemented by a class in the managed environment, the .NET Framework supplies implementations of the COM interfaces listed in the following table on behalf of the object.</span></span> <span data-ttu-id="62620-127">Uma classe .NET pode substituir o comportamento padrão fornecendo sua própria implementação dessas interfaces.</span><span class="sxs-lookup"><span data-stu-id="62620-127">A .NET class can override the default behavior by providing its own implementation of these interfaces.</span></span> <span data-ttu-id="62620-128">No entanto, o tempo de execução sempre fornece a implementação para as interfaces **IUnknown** e **IDispatch**.</span><span class="sxs-lookup"><span data-stu-id="62620-128">However, the runtime always provides the implementation for the **IUnknown** and **IDispatch** interfaces.</span></span>

|<span data-ttu-id="62620-129">Interface</span><span class="sxs-lookup"><span data-stu-id="62620-129">Interface</span></span>|<span data-ttu-id="62620-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="62620-130">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="62620-131">**IDispatch**</span><span class="sxs-lookup"><span data-stu-id="62620-131">**IDispatch**</span></span>|<span data-ttu-id="62620-132">Fornece um mecanismo de associação tardia ao tipo.</span><span class="sxs-lookup"><span data-stu-id="62620-132">Provides a mechanism for late binding to type.</span></span>|
|<span data-ttu-id="62620-133">**IErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="62620-133">**IErrorInfo**</span></span>|<span data-ttu-id="62620-134">Fornece uma descrição textual do erro, sua origem, um arquivo de Ajuda, um contexto de Ajuda e o GUID da interface que definiu o erro (sempre **GUID_NULL** para classes do .NET).</span><span class="sxs-lookup"><span data-stu-id="62620-134">Provides a textual description of the error, its source, a Help file, Help context, and the GUID of the interface that defined the error (always **GUID_NULL** for .NET classes).</span></span>|
|<span data-ttu-id="62620-135">**IProvideClassInfo**</span><span class="sxs-lookup"><span data-stu-id="62620-135">**IProvideClassInfo**</span></span>|<span data-ttu-id="62620-136">Permite aos clientes COM obter acesso à interface **ITypeInfo** implementada por uma classe gerenciada.</span><span class="sxs-lookup"><span data-stu-id="62620-136">Enables COM clients to gain access to the **ITypeInfo** interface implemented by a managed class.</span></span>|
|<span data-ttu-id="62620-137">**ISupportErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="62620-137">**ISupportErrorInfo**</span></span>|<span data-ttu-id="62620-138">Permite a um cliente COM determinar se o objeto gerenciado dá suporte à interface **IErrorInfo**.</span><span class="sxs-lookup"><span data-stu-id="62620-138">Enables a COM client to determine whether the managed object supports the **IErrorInfo** interface.</span></span> <span data-ttu-id="62620-139">Nesse caso, permite ao cliente obter um ponteiro para o último objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="62620-139">If so, enables the client to obtain a pointer to the latest exception object.</span></span> <span data-ttu-id="62620-140">Todos os tipos gerenciados dão suporte à interface **IErrorInfo**.</span><span class="sxs-lookup"><span data-stu-id="62620-140">All managed types support the **IErrorInfo** interface.</span></span>|
|<span data-ttu-id="62620-141">**ITypeInfo**</span><span class="sxs-lookup"><span data-stu-id="62620-141">**ITypeInfo**</span></span>|<span data-ttu-id="62620-142">Fornece informações de tipo de uma classe que são exatamente iguais às informações de tipo produzidas pelo Tlbexp.exe.</span><span class="sxs-lookup"><span data-stu-id="62620-142">Provides type information for a class that is exactly the same as the type information produced by Tlbexp.exe.</span></span>|
|<span data-ttu-id="62620-143">**IUnknown**</span><span class="sxs-lookup"><span data-stu-id="62620-143">**IUnknown**</span></span>|<span data-ttu-id="62620-144">Fornece a implementação padrão da interface **IUnknown** com a qual o cliente COM gerencia o tempo de vida do CCW e fornece a coerção de tipo.</span><span class="sxs-lookup"><span data-stu-id="62620-144">Provides the standard implementation of the **IUnknown** interface with which the COM client manages the lifetime of the CCW and provides type coercion.</span></span>|

 <span data-ttu-id="62620-145">Uma classe gerenciada também pode fornecer as interfaces COM descritas na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="62620-145">A managed class can also provide the COM interfaces described in the following table.</span></span>

|<span data-ttu-id="62620-146">Interface</span><span class="sxs-lookup"><span data-stu-id="62620-146">Interface</span></span>|<span data-ttu-id="62620-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="62620-147">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="62620-148">A interface de classe (\_*classname*)</span><span class="sxs-lookup"><span data-stu-id="62620-148">The (\_*classname*) class interface</span></span>|<span data-ttu-id="62620-149">Interface, exposta pelo tempo de execução e não definida explicitamente, que expõe todas as interfaces públicas, métodos, propriedades e campos que são expostos explicitamente em um objeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="62620-149">Interface, exposed by the runtime and not explicitly defined, that exposes all public interfaces, methods, properties, and fields that are explicitly exposed on a managed object.</span></span>|
|<span data-ttu-id="62620-150">**IConnectionPoint** e **IConnectionPointContainer**</span><span class="sxs-lookup"><span data-stu-id="62620-150">**IConnectionPoint** and **IConnectionPointContainer**</span></span>|<span data-ttu-id="62620-151">Interface para objetos que dão origem a eventos baseados em representante (uma interface para o registro de assinantes do evento).</span><span class="sxs-lookup"><span data-stu-id="62620-151">Interface for objects that source delegate-based events (an interface for registering event subscribers).</span></span>|
|<span data-ttu-id="62620-152">**IDispatchEx**</span><span class="sxs-lookup"><span data-stu-id="62620-152">**IDispatchEx**</span></span>|<span data-ttu-id="62620-153">Interface fornecida pelo tempo de execução se a classe implementa **IExpando**.</span><span class="sxs-lookup"><span data-stu-id="62620-153">Interface supplied by the runtime if the class implements **IExpando**.</span></span> <span data-ttu-id="62620-154">A interface **IDispatchEx** é uma extensão da interface **IDispatch** que, ao contrário de **IDispatch**, permite a enumeração, adição, exclusão e chamada de membros que diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="62620-154">The **IDispatchEx** interface is an extension of the **IDispatch** interface that, unlike **IDispatch**, enables enumeration, addition, deletion, and case-sensitive calling of members.</span></span>|
|<span data-ttu-id="62620-155">**IEnumVARIANT**</span><span class="sxs-lookup"><span data-stu-id="62620-155">**IEnumVARIANT**</span></span>|<span data-ttu-id="62620-156">Interface para classes de tipo de coleção, que enumera os objetos na coleção, se a classe implementa **IEnumerable**.</span><span class="sxs-lookup"><span data-stu-id="62620-156">Interface for collection-type classes, which enumerates the objects in the collection if the class implements **IEnumerable**.</span></span>|

## <a name="introducing-the-class-interface"></a><span data-ttu-id="62620-157">Introdução à interface de classe</span><span class="sxs-lookup"><span data-stu-id="62620-157">Introducing the class interface</span></span>

<span data-ttu-id="62620-158">A interface de classe, que não é definida explicitamente no código gerenciado, é uma interface que expõe todos os métodos públicos, propriedades, campos e eventos que são expostos explicitamente no objeto .NET.</span><span class="sxs-lookup"><span data-stu-id="62620-158">The class interface, which is not explicitly defined in managed code, is an interface that exposes all public methods, properties, fields, and events that are explicitly exposed on the .NET object.</span></span> <span data-ttu-id="62620-159">Essa interface pode ser uma interface dupla ou somente de expedição.</span><span class="sxs-lookup"><span data-stu-id="62620-159">This interface can be a dual or dispatch-only interface.</span></span> <span data-ttu-id="62620-160">A interface de classe recebe o nome da própria classe do .NET, precedido por um sublinhado.</span><span class="sxs-lookup"><span data-stu-id="62620-160">The class interface receives the name of the .NET class itself, preceded by an underscore.</span></span> <span data-ttu-id="62620-161">Por exemplo, para a classe Mammal, a interface de classe é \_Mammal.</span><span class="sxs-lookup"><span data-stu-id="62620-161">For example, for class Mammal, the class interface is \_Mammal.</span></span>

<span data-ttu-id="62620-162">Para classes derivadas, a interface de classe também expõe todos os métodos públicos, propriedades e campos da classe base.</span><span class="sxs-lookup"><span data-stu-id="62620-162">For derived classes, the class interface also exposes all public methods, properties, and fields of the base class.</span></span> <span data-ttu-id="62620-163">A classe derivada também expõe uma interface de classe para cada classe base.</span><span class="sxs-lookup"><span data-stu-id="62620-163">The derived class also exposes a class interface for each base class.</span></span> <span data-ttu-id="62620-164">Por exemplo, se a classe Mammal estende a classe MammalSuperclass, que, por sua vez, estende System.Object, o objeto do .NET expõe para os clientes COM três interfaces de classe chamadas \_Mammal, \_MammalSuperclass e \_Object.</span><span class="sxs-lookup"><span data-stu-id="62620-164">For example, if class Mammal extends class MammalSuperclass, which itself extends System.Object, the .NET object exposes to COM clients three class interfaces named \_Mammal, \_MammalSuperclass, and \_Object.</span></span>

<span data-ttu-id="62620-165">Por exemplo, considere a seguinte classe do .NET:</span><span class="sxs-lookup"><span data-stu-id="62620-165">For example, consider the following .NET class:</span></span>

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
    public void Eat() {}
    public void Breathe() {}
    public void Sleep() {}
}
```

<span data-ttu-id="62620-166">O cliente COM pode obter um ponteiro para uma interface de classe chamado `_Mammal`, que é descrito na biblioteca de tipos gerada pela ferramenta [Exportador da Biblioteca de Tipos (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="62620-166">The COM client can obtain a pointer to a class interface named `_Mammal`, which is described in the type library that the [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) tool generates.</span></span> <span data-ttu-id="62620-167">Se a classe `Mammal` tiver implementado uma ou mais interfaces, as interfaces aparecerão na coclass.</span><span class="sxs-lookup"><span data-stu-id="62620-167">If the `Mammal` class implemented one or more interfaces, the interfaces would appear under the coclass.</span></span>

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

<span data-ttu-id="62620-168">A geração da interface de classe é opcional.</span><span class="sxs-lookup"><span data-stu-id="62620-168">Generating the class interface is optional.</span></span> <span data-ttu-id="62620-169">Por padrão, a interoperabilidade COM gera uma interface somente de expedição para cada classe exportada para uma biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="62620-169">By default, COM interop generates a dispatch-only interface for each class you export to a type library.</span></span> <span data-ttu-id="62620-170">É possível impedir ou modificar a criação automática dessa interface aplicando o <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> à classe.</span><span class="sxs-lookup"><span data-stu-id="62620-170">You can prevent or modify the automatic creation of this interface by applying the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> to your class.</span></span> <span data-ttu-id="62620-171">Embora a interface de classe possa facilitar a tarefa de exposição das classes gerenciadas ao COM, seus usos são limitados.</span><span class="sxs-lookup"><span data-stu-id="62620-171">Although the class interface can ease the task of exposing managed classes to COM, its uses are limited.</span></span>

> [!CAUTION]
> <span data-ttu-id="62620-172">O uso da interface de classe, em vez da definição explícita de sua própria, pode complicar o controle futuro de versão da classe gerenciada.</span><span class="sxs-lookup"><span data-stu-id="62620-172">Using the class interface, instead of explicitly defining your own, can complicate the future versioning of your managed class.</span></span> <span data-ttu-id="62620-173">Leia as diretrizes a seguir antes de usar a interface de classe.</span><span class="sxs-lookup"><span data-stu-id="62620-173">Please read the following guidelines before using the class interface.</span></span>

### <a name="define-an-explicit-interface-for-com-clients-to-use-rather-than-generating-the-class-interface"></a><span data-ttu-id="62620-174">Defina uma interface explícita para uso dos clientes COM, em vez de gerar a interface de classe.</span><span class="sxs-lookup"><span data-stu-id="62620-174">Define an explicit interface for COM clients to use rather than generating the class interface.</span></span>

<span data-ttu-id="62620-175">Como a interoperabilidade COM gera uma interface de classe automaticamente, alterações posteriores à versão na classe podem alterar o layout da interface de classe exposta pelo Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="62620-175">Because COM interop generates a class interface automatically, post-version changes to your class can alter the layout of the class interface exposed by the common language runtime.</span></span> <span data-ttu-id="62620-176">Já que os clientes COM não estão normalmente preparados para manipular as alterações no layout de uma interface, eles são interrompidos se o layout de membro da classe é alterado.</span><span class="sxs-lookup"><span data-stu-id="62620-176">Since COM clients are typically unprepared to handle changes in the layout of an interface, they break if you change the member layout of the class.</span></span>

<span data-ttu-id="62620-177">Esta diretriz reforça a noção de que as interfaces expostas para os clientes COM devem permanecer inalteráveis.</span><span class="sxs-lookup"><span data-stu-id="62620-177">This guideline reinforces the notion that interfaces exposed to COM clients must remain unchangeable.</span></span> <span data-ttu-id="62620-178">Para reduzir o risco de interromper os clientes COM reordenando inadvertidamente o layout da interface, isole todas as alterações na classe do layout da interface definindo interfaces explicitamente.</span><span class="sxs-lookup"><span data-stu-id="62620-178">To reduce the risk of breaking COM clients by inadvertently reordering the interface layout, isolate all changes to the class from the interface layout by explicitly defining interfaces.</span></span>

<span data-ttu-id="62620-179">Use o **ClassInterfaceAttribute** para desativar a geração automática da interface de classe e implementar uma interface explícita para a classe, como mostra o seguinte fragmento de código:</span><span class="sxs-lookup"><span data-stu-id="62620-179">Use the **ClassInterfaceAttribute** to disengage the automatic generation of the class interface and implement an explicit interface for the class, as the following code fragment shows:</span></span>

```vb
<ClassInterface(ClassInterfaceType.None)>Public Class LoanApp
    Implements IExplicit
    Sub M() Implements IExplicit.M
…
End Class
```

```csharp
[ClassInterface(ClassInterfaceType.None)]
public class LoanApp : IExplicit
{
    int IExplicit.M() { return 0; }
}
```

<span data-ttu-id="62620-180">O valor **ClassInterfaceType.None** impede que a interface de classe seja gerada quando os metadados da classe são exportados para uma biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="62620-180">The **ClassInterfaceType.None** value prevents the class interface from being generated when the class metadata is exported to a type library.</span></span> <span data-ttu-id="62620-181">No exemplo anterior, os clientes COM podem acessar a classe `LoanApp` somente pela interface `IExplicit`.</span><span class="sxs-lookup"><span data-stu-id="62620-181">In the preceding example, COM clients can access the `LoanApp` class only through the `IExplicit` interface.</span></span>

### <a name="avoid-caching-dispatch-identifiers-dispids"></a><span data-ttu-id="62620-182">Evitar o cache de identificadores de expedição (DispIds)</span><span class="sxs-lookup"><span data-stu-id="62620-182">Avoid caching dispatch identifiers (DispIds)</span></span>

<span data-ttu-id="62620-183">O uso da interface de classe é uma opção aceitável para os clientes com script, os clientes do Microsoft Visual Basic 6.0 ou qualquer cliente de associação tardia que não armazena em cache os DispIds dos membros da interface.</span><span class="sxs-lookup"><span data-stu-id="62620-183">Using the class interface is an acceptable option for scripted clients, Microsoft Visual Basic 6.0 clients, or any late-bound client that does not cache the DispIds of interface members.</span></span> <span data-ttu-id="62620-184">Os DispIds identificam os membros da interface para habilitar a associação tardia.</span><span class="sxs-lookup"><span data-stu-id="62620-184">DispIds identify interface members to enable late binding.</span></span>

<span data-ttu-id="62620-185">Para a interface de classe, a geração dos DispIds se baseia na posição do membro na interface.</span><span class="sxs-lookup"><span data-stu-id="62620-185">For the class interface, generation of DispIds is based on the position of the member in the interface.</span></span> <span data-ttu-id="62620-186">Se você alterar a ordem do membro e exportar a classe para uma biblioteca de tipos, você alterará os DispIds gerados na interface de classe.</span><span class="sxs-lookup"><span data-stu-id="62620-186">If you change the order of the member and export the class to a type library, you will alter the DispIds generated in the class interface.</span></span>

<span data-ttu-id="62620-187">Para evitar a interrupção de clientes COM de associação tardia ao usar a interface de classe, aplique o **ClassInterfaceAttribute** ao valor **ClassInterfaceType.AutoDispatch**.</span><span class="sxs-lookup"><span data-stu-id="62620-187">To avoid breaking late-bound COM clients when using the class interface, apply the **ClassInterfaceAttribute** with the **ClassInterfaceType.AutoDispatch** value.</span></span> <span data-ttu-id="62620-188">Esse valor implementa uma interface de classe somente de expedição, mas omite a descrição da interface na biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="62620-188">This value implements a dispatch-only class interface, but omits the interface description from the type library.</span></span> <span data-ttu-id="62620-189">Sem uma descrição da interface, os clientes não conseguem armazenar em cache os DispIds em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="62620-189">Without an interface description, clients are unable to cache DispIds at compile time.</span></span> <span data-ttu-id="62620-190">Embora esse seja o tipo de interface padrão para a interface de classe, é possível aplicar o valor do atributo explicitamente.</span><span class="sxs-lookup"><span data-stu-id="62620-190">Although this is the default interface type for the class interface, you can apply the attribute value explicitly.</span></span>

```vb
<ClassInterface(ClassInterfaceType.AutoDispatch)> Public Class LoanApp
    Implements IAnother
    Sub M() Implements IAnother.M
…
End Class
```

```csharp
[ClassInterface(ClassInterfaceType.AutoDispatch)]
public class LoanApp
{
    public int M() { return 0; }
}
```

<span data-ttu-id="62620-191">Para obter o DispId de um membro da interface em tempo de execução, os clientes COM podem chamar **IDispatch.GetIdsOfNames**.</span><span class="sxs-lookup"><span data-stu-id="62620-191">To get the DispId of an interface member at run time, COM clients can call **IDispatch.GetIdsOfNames**.</span></span> <span data-ttu-id="62620-192">Para invocar um método na interface, passe o DispId retornado como um argumento para **IDispatch.Invoke**.</span><span class="sxs-lookup"><span data-stu-id="62620-192">To invoke a method on the interface, pass the returned DispId as an argument to **IDispatch.Invoke**.</span></span>

### <a name="restrict-using-the-dual-interface-option-for-the-class-interface"></a><span data-ttu-id="62620-193">Restrinja o uso da opção de interface dupla para a interface de classe.</span><span class="sxs-lookup"><span data-stu-id="62620-193">Restrict using the dual interface option for the class interface.</span></span>

<span data-ttu-id="62620-194">Interfaces duplas permitem a associação inicial e tardia a membros da interface por clientes COM.</span><span class="sxs-lookup"><span data-stu-id="62620-194">Dual interfaces enable early and late binding to interface members by COM clients.</span></span> <span data-ttu-id="62620-195">Em tempo de design e durante o teste, talvez seja útil definir a interface de classe como dupla.</span><span class="sxs-lookup"><span data-stu-id="62620-195">At design time and during testing, you might find it useful to set the class interface to dual.</span></span> <span data-ttu-id="62620-196">Para uma classe gerenciada (e suas classes base) que nunca serão modificadas, essa opção também é aceitável.</span><span class="sxs-lookup"><span data-stu-id="62620-196">For a managed class (and its base classes) that will never be modified, this option is also acceptable.</span></span> <span data-ttu-id="62620-197">Em todos os outros casos, evite definir a interface de classe como dupla.</span><span class="sxs-lookup"><span data-stu-id="62620-197">In all other cases, avoid setting the class interface to dual.</span></span>

<span data-ttu-id="62620-198">Uma interface dupla gerada automaticamente pode ser apropriada em casos raros. No entanto, com mais frequência, ela cria complexidade relacionada à versão.</span><span class="sxs-lookup"><span data-stu-id="62620-198">An automatically generated dual interface might be appropriate in rare cases; however, more often it creates version-related complexity.</span></span> <span data-ttu-id="62620-199">Por exemplo, os clientes COM que usam a interface de classe de uma classe derivada podem ser facilmente interrompidos com alterações na classe base.</span><span class="sxs-lookup"><span data-stu-id="62620-199">For example, COM clients using the class interface of a derived class can easily break with changes to the base class.</span></span> <span data-ttu-id="62620-200">Quando um terceiro fornece a classe base, o layout da interface de classe fica fora de seu controle.</span><span class="sxs-lookup"><span data-stu-id="62620-200">When a third party provides the base class, the layout of the class interface is out of your control.</span></span> <span data-ttu-id="62620-201">Além disso, ao contrário de uma interface somente de expedição, uma interface dupla (**ClassInterfaceType.AutoDual**) fornece uma descrição da interface de classe na biblioteca de tipos exportada.</span><span class="sxs-lookup"><span data-stu-id="62620-201">Further, unlike a dispatch-only interface, a dual interface (**ClassInterfaceType.AutoDual**) provides a description of the class interface in the exported type library.</span></span> <span data-ttu-id="62620-202">Uma descrição como essa incentiva os clientes de associação tardia a armazenarem em cache os DispIds em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="62620-202">Such a description encourages late-bound clients to cache DispIds at compile time.</span></span>

### <a name="ensure-that-all-com-event-notifications-are-late-bound"></a><span data-ttu-id="62620-203">Verifique se todas as notificações de evento COM têm associação tardia.</span><span class="sxs-lookup"><span data-stu-id="62620-203">Ensure that all COM event notifications are late-bound.</span></span>

<span data-ttu-id="62620-204">Por padrão, informações de tipo COM são incorporadas diretamente em assemblies gerenciados, o que elimina a necessidade de PIAS (assemblies de interoperabilidade primários).</span><span class="sxs-lookup"><span data-stu-id="62620-204">By default, COM type information is embedded directly into managed assemblies, which eliminates the need for primary interop assemblies (PIAs).</span></span> <span data-ttu-id="62620-205">No entanto, uma das limitações das informações de tipo inseridas é que elas não dão suporte a entrega de notificações de eventos COM por chamadas vtable early-bound, mas dá suporte apenas a chamadas `IDispatch::Invoke` de associação tardia.</span><span class="sxs-lookup"><span data-stu-id="62620-205">However, one of the limitations of embedded type information is that it does not supported delivery of COM event notifications by early-bound vtable calls, but only supports late-bound `IDispatch::Invoke` calls.</span></span>

<span data-ttu-id="62620-206">Se o seu aplicativo exigir chamadas early-bound para métodos de interface de eventos COM, defina a propriedade **Embed Interop Types** no Visual Studio como `true`, ou inclua o seguinte elemento no arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="62620-206">If your application requires early-bound calls to COM event interface methods, you can set the **Embed Interop Types** property in Visual Studio to `true`, or include the following element in your project file:</span></span>

```xml
<EmbedInteropTypes>True</EmbedInteropTypes>
```

## <a name="see-also"></a><span data-ttu-id="62620-207">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62620-207">See also</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [<span data-ttu-id="62620-208">Wrappers COM</span><span class="sxs-lookup"><span data-stu-id="62620-208">COM Wrappers</span></span>](com-wrappers.md)
- [<span data-ttu-id="62620-209">Expondo componentes do .NET Framework ao COM</span><span class="sxs-lookup"><span data-stu-id="62620-209">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="62620-210">Qualificando tipos .NET para interoperação</span><span class="sxs-lookup"><span data-stu-id="62620-210">Qualifying .NET Types for Interoperation</span></span>](qualifying-net-types-for-interoperation.md)
- [<span data-ttu-id="62620-211">RCW (Runtime Callable Wrapper)</span><span class="sxs-lookup"><span data-stu-id="62620-211">Runtime Callable Wrapper</span></span>](runtime-callable-wrapper.md)
