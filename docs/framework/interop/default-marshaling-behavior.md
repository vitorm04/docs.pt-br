---
title: Comportamento de marshaling padrão
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, default
- interoperation with unmanaged code, marshaling
- marshaling behavior
ms.assetid: c0a9bcdf-3df8-4db3-b1b6-abbdb2af809a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f5fef84250f9dbc10a921a6844f7020c72835cea
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457361"
---
# <a name="default-marshaling-behavior"></a><span data-ttu-id="9dcfb-102">Comportamento de marshaling padrão</span><span class="sxs-lookup"><span data-stu-id="9dcfb-102">Default Marshaling Behavior</span></span>
<span data-ttu-id="9dcfb-103">O marshaling de interoperabilidade opera em regras que determinam como os dados associados aos parâmetros de método se comportam, conforme eles passam entre a memória gerenciada e não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-103">Interop marshaling operates on rules that dictate how data associated with method parameters behaves as it passes between managed and unmanaged memory.</span></span> <span data-ttu-id="9dcfb-104">Essas regras internas controlam atividades de marshaling como transformações de tipo de dados, se um receptor pode alterar os dados passados para ele e retornar essas alterações ao chamador e em quais circunstâncias o marshaler fornece otimizações de desempenho.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-104">These built-in rules control such marshaling activities as data type transformations, whether a callee can change data passed to it and return those changes to the caller, and under which circumstances the marshaler provides performance optimizations.</span></span>  
  
 <span data-ttu-id="9dcfb-105">Esta seção identifica as características comportamentais padrão do serviço de marshaling de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-105">This section identifies the default behavioral characteristics of the interop marshaling service.</span></span> <span data-ttu-id="9dcfb-106">Ela apresenta informações detalhadas sobre o marshaling de matrizes, tipos boolianos, tipos char, representantes, classes, objetos, cadeias de caracteres e estruturas.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-106">It presents detailed information on marshaling arrays, Boolean types, char types, delegates, classes, objects, strings, and structures.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9dcfb-107">Não há suporte para o marshaling de tipos genéricos.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-107">Marshaling of generic types is not supported.</span></span> <span data-ttu-id="9dcfb-108">Para obter mais informações, consulte [Interoperando com tipos genéricos](https://msdn.microsoft.com/library/26b88e03-085b-4b53-94ba-a5a9c709ce58(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="9dcfb-108">For more information see, [Interoperating Using Generic Types](https://msdn.microsoft.com/library/26b88e03-085b-4b53-94ba-a5a9c709ce58(v=vs.100)).</span></span>  
  
## <a name="memory-management-with-the-interop-marshaler"></a><span data-ttu-id="9dcfb-109">Gerenciamento de memória com o marshaler de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="9dcfb-109">Memory management with the interop marshaler</span></span>  
 <span data-ttu-id="9dcfb-110">O marshaler de interoperabilidade sempre tenta liberar a memória alocada pelo código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-110">The interop marshaler always attempts to free memory allocated by unmanaged code.</span></span> <span data-ttu-id="9dcfb-111">Esse comportamento está em conformidade com as regras de gerenciamento da memória COM, mas é diferente das regras que regem o C++ nativo.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-111">This behavior complies with COM memory management rules, but differs from the rules that govern native C++.</span></span>  
  
 <span data-ttu-id="9dcfb-112">Poderá haver confusão se você antecipar o comportamento do C++ nativo (sem liberação de memória) ao usar a invocação de plataforma, que libera a memória para ponteiros automaticamente.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-112">Confusion can arise if you anticipate native C++ behavior (no memory freeing) when using platform invoke, which automatically frees memory for pointers.</span></span> <span data-ttu-id="9dcfb-113">Por exemplo, a chamada do método não gerenciado a seguir em uma DLL do C++ não libera qualquer memória automaticamente.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-113">For example, calling the following unmanaged method from a C++ DLL does not automatically free any memory.</span></span>  
  
### <a name="unmanaged-signature"></a><span data-ttu-id="9dcfb-114">Assinatura não gerenciada</span><span class="sxs-lookup"><span data-stu-id="9dcfb-114">Unmanaged signature</span></span>  
  
```  
BSTR MethodOne (BSTR b) {  
     return b;  
}  
```  
  
 <span data-ttu-id="9dcfb-115">No entanto, se você definir o método como um protótipo de invocação de plataforma, substituir cada tipo **BSTR** por um tipo <xref:System.String> e chamar `MethodOne`, o Common Language Runtime tentará liberar `b` duas vezes.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-115">However, if you define the method as a platform invoke prototype, replace each **BSTR** type with a <xref:System.String> type, and call `MethodOne`, the common language runtime attempts to free `b` twice.</span></span> <span data-ttu-id="9dcfb-116">Altere o comportamento de marshaling usando tipos <xref:System.IntPtr>, em vez de tipos **String**.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-116">You can change the marshaling behavior by using <xref:System.IntPtr> types rather than **String** types.</span></span>  
  
 <span data-ttu-id="9dcfb-117">O tempo de execução sempre usa o método **CoTaskMemFree** para liberar memória.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-117">The runtime always uses the **CoTaskMemFree** method to free memory.</span></span> <span data-ttu-id="9dcfb-118">Se a memória com a qual você está trabalhando não foi alocada com o método **CoTaskMemAlloc**, use um **IntPtr** e libere a memória manualmente usando o método apropriado.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-118">If the memory you are working with was not allocated with the **CoTaskMemAlloc** method, you must use an **IntPtr** and free the memory manually using the appropriate method.</span></span> <span data-ttu-id="9dcfb-119">Da mesma forma, evite a liberação automática de memória em situações em que a memória nunca deve ser liberada, como ao usar a função **GetCommandLine** no Kernel32.dll, que retorna um ponteiro para a memória do kernel.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-119">Similarly, you can avoid automatic memory freeing in situations where memory should never be freed, such as when using the **GetCommandLine** function from Kernel32.dll, which returns a pointer to kernel memory.</span></span> <span data-ttu-id="9dcfb-120">Para obter detalhes sobre como liberar a memória manualmente, consulte a [Amostra de buffers](http://msdn.microsoft.com/library/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="9dcfb-120">For details on manually freeing memory, see the [Buffers Sample](http://msdn.microsoft.com/library/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5(v=vs.100)).</span></span>  
  
## <a name="default-marshaling-for-classes"></a><span data-ttu-id="9dcfb-121">Marshaling padrão para classes</span><span class="sxs-lookup"><span data-stu-id="9dcfb-121">Default marshaling for classes</span></span>  
 <span data-ttu-id="9dcfb-122">As classes podem ter o marshaling realizado somente pela interoperabilidade COM e sempre têm o marshaling realizado como interfaces.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-122">Classes can be marshaled only by COM interop and are always marshaled as interfaces.</span></span> <span data-ttu-id="9dcfb-123">Em alguns casos, a interface usada para realizar marshaling da classe é conhecida como a interface de classe.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-123">In some cases the interface used to marshal the class is known as the class interface.</span></span> <span data-ttu-id="9dcfb-124">Para obter informações sobre como substituir a interface de classe por uma interface de sua preferência, confira [Apresentando a interface de classe](com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="9dcfb-124">For information about overriding the class interface with an interface of your choice, see [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
### <a name="passing-classes-to-com"></a><span data-ttu-id="9dcfb-125">Passando classes para o COM</span><span class="sxs-lookup"><span data-stu-id="9dcfb-125">Passing Classes to COM</span></span>  
 <span data-ttu-id="9dcfb-126">Quando uma classe gerenciada é passada para o COM, o marshaler de interoperabilidade encapsula a classe automaticamente com um proxy COM e passa a interface de classe produzida pelo proxy para a chamada de método COM.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-126">When a managed class is passed to COM, the interop marshaler automatically wraps the class with a COM proxy and passes the class interface produced by the proxy to the COM method call.</span></span> <span data-ttu-id="9dcfb-127">Em seguida, o proxy delega todas as chamadas na interface de classe novamente para o objeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-127">The proxy then delegates all calls on the class interface back to the managed object.</span></span> <span data-ttu-id="9dcfb-128">O proxy também expõe interfaces que não são implementadas pela classe explicitamente.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-128">The proxy also exposes other interfaces that are not explicitly implemented by the class.</span></span> <span data-ttu-id="9dcfb-129">O proxy implementa automaticamente interfaces como **IUnknown** e **IDispatch** em nome da classe.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-129">The proxy automatically implements interfaces such as **IUnknown** and **IDispatch** on behalf of the class.</span></span>  
  
### <a name="passing-classes-to-net-code"></a><span data-ttu-id="9dcfb-130">Passando classes para o código do .NET</span><span class="sxs-lookup"><span data-stu-id="9dcfb-130">Passing Classes to .NET Code</span></span>  
 <span data-ttu-id="9dcfb-131">As coclasses não são normalmente usadas como argumentos de método no COM.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-131">Coclasses are not typically used as method arguments in COM.</span></span> <span data-ttu-id="9dcfb-132">Em vez disso, uma interface padrão geralmente é passada no lugar da coclass.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-132">Instead, a default interface is usually passed in place of the coclass.</span></span>  
  
 <span data-ttu-id="9dcfb-133">Quando uma interface é passada para um código gerenciado, o marshaler de interoperabilidade é responsável por encapsular a interface com o wrapper apropriado e passar o wrapper para o método gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-133">When an interface is passed into managed code, the interop marshaler is responsible for wrapping the interface with the proper wrapper and passing the wrapper to the managed method.</span></span> <span data-ttu-id="9dcfb-134">Pode ser difícil determinar quais wrapper usar.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-134">Determining which wrapper to use can be difficult.</span></span> <span data-ttu-id="9dcfb-135">Cada instância de um objeto COM tem um único wrapper exclusivo, não importa quantas interfaces são implementadas pelo objeto.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-135">Every instance of a COM object has a single, unique wrapper, no matter how many interfaces the object implements.</span></span> <span data-ttu-id="9dcfb-136">Por exemplo, um único objeto COM que implementa cinco interfaces distintas tem apenas um wrapper.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-136">For example, a single COM object that implements five distinct interfaces has only one wrapper.</span></span> <span data-ttu-id="9dcfb-137">O mesmo wrapper expõe todas as cinco interfaces.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-137">The same wrapper exposes all five interfaces.</span></span> <span data-ttu-id="9dcfb-138">Se duas instâncias do objeto COM são criadas, duas instâncias do wrapper são criadas.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-138">If two instances of the COM object are created, then two instances of the wrapper are created.</span></span>  
  
 <span data-ttu-id="9dcfb-139">Para que o wrapper mantenha o mesmo tipo em todo seu tempo de vida, o marshaler de interoperabilidade deve identificar o wrapper correto na primeira vez que uma interface exposta pelo objeto é passada por meio do marshaler.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-139">For the wrapper to maintain the same type throughout its lifetime, the interop marshaler must identify the correct wrapper the first time an interface exposed by the object is passed through the marshaler.</span></span> <span data-ttu-id="9dcfb-140">O marshaler identifica o objeto examinando uma das interfaces implementadas pelo objeto.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-140">The marshaler identifies the object by looking at one of the interfaces the object implements.</span></span>  
  
 <span data-ttu-id="9dcfb-141">Por exemplo, o marshaler determina que o wrapper de classe deve ser usado para encapsular a interface que foi passada para o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-141">For example, the marshaler determines that the class wrapper should be used to wrap the interface that was passed into managed code.</span></span> <span data-ttu-id="9dcfb-142">Quando a interface é passada pelo marshaler pela primeira vez, o marshaler verifica se a interface está sendo recebida de um objeto conhecido.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-142">When the interface is first passed through the marshaler, the marshaler checks whether the interface is coming from a known object.</span></span> <span data-ttu-id="9dcfb-143">Essa verificação ocorre em duas situações:</span><span class="sxs-lookup"><span data-stu-id="9dcfb-143">This check occurs in two situations:</span></span>  
  
-   <span data-ttu-id="9dcfb-144">Uma interface está sendo implementada por outro objeto gerenciado que foi passado para o COM em outro lugar.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-144">An interface is being implemented by another managed object that was passed to COM elsewhere.</span></span> <span data-ttu-id="9dcfb-145">O marshaler pode identificar prontamente as interfaces expostas pelos objetos gerenciados e pode fazer a correspondência da interface com o objeto gerenciado que fornece a implementação.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-145">The marshaler can readily identify interfaces exposed by managed objects and is able to match the interface with the managed object that provides the implementation.</span></span> <span data-ttu-id="9dcfb-146">Em seguida, o objeto gerenciado é passado para o método e nenhum wrapper é necessário.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-146">The managed object is then passed to the method and no wrapper is needed.</span></span>  
  
-   <span data-ttu-id="9dcfb-147">Um objeto que já foi encapsulado está implementando a interface.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-147">An object that has already been wrapped is implementing the interface.</span></span> <span data-ttu-id="9dcfb-148">Para determinar se esse é o caso, o marshaler consulta o objeto em busca de sua interface **IUnknown** e compara a interface retornada com as interfaces de outros objetos que já estão encapsulados.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-148">To determine whether this is the case, the marshaler queries the object for its **IUnknown** interface and compares the returned interface to the interfaces of other objects that are already wrapped.</span></span> <span data-ttu-id="9dcfb-149">Se a interface for a mesma de outro wrapper, os objetos terão a mesma identidade e o wrapper existente será passado para o método.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-149">If the interface is the same as that of another wrapper, the objects have the same identity and the existing wrapper is passed to the method.</span></span>  
  
 <span data-ttu-id="9dcfb-150">Se uma interface não for de um objeto conhecido, o marshaler fará o seguinte:</span><span class="sxs-lookup"><span data-stu-id="9dcfb-150">If an interface is not from a known object, the marshaler does the following:</span></span>  
  
1.  <span data-ttu-id="9dcfb-151">O marshaler consulta o objeto em busca da interface **IProvideClassInfo2**.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-151">The marshaler queries the object for the **IProvideClassInfo2** interface.</span></span> <span data-ttu-id="9dcfb-152">Se for fornecido, o marshaler usará o CLSID retornado de **IProvideClassInfo2.GetGUID** para identificar a coclass que fornece a interface.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-152">If provided, the marshaler uses the CLSID returned from **IProvideClassInfo2.GetGUID** to identify the coclass providing the interface.</span></span> <span data-ttu-id="9dcfb-153">Com o CLSID, o marshaler pode localizar o wrapper no Registro, caso o assembly já tenha sido registrado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-153">With the CLSID, the marshaler can locate the wrapper from the registry if the assembly has previously been registered.</span></span>  
  
2.  <span data-ttu-id="9dcfb-154">O marshaler consulta a interface em busca da interface **IProvideClassInfo**.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-154">The marshaler queries the interface for the **IProvideClassInfo** interface.</span></span> <span data-ttu-id="9dcfb-155">Se for fornecido, o marshaler usará o **ITypeInfo** retornado de **IProvideClassInfo.GetClassinfo** para determinar o CLSID da classe que expõe a interface.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-155">If provided, the marshaler uses the **ITypeInfo** returned from **IProvideClassInfo.GetClassinfo** to determine the CLSID of the class exposing the interface.</span></span> <span data-ttu-id="9dcfb-156">O marshaler pode usar o CLSID para localizar os metadados do wrapper.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-156">The marshaler can use the CLSID to locate the metadata for the wrapper.</span></span>  
  
3.  <span data-ttu-id="9dcfb-157">Se o marshaler ainda não puder identificar a classe, ele encapsulará a interface com uma classe wrapper genérica chamada **System.__ComObject**.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-157">If the marshaler still cannot identify the class, it wraps the interface with a generic wrapper class called **System.__ComObject**.</span></span>  
  
## <a name="default-marshaling-for-delegates"></a><span data-ttu-id="9dcfb-158">Marshaling padrão para representantes</span><span class="sxs-lookup"><span data-stu-id="9dcfb-158">Default marshaling for delegates</span></span>  
 <span data-ttu-id="9dcfb-159">Um representante gerenciado tem o marshaling realizado como uma interface COM ou como um ponteiro de função, com base no mecanismo de chamada:</span><span class="sxs-lookup"><span data-stu-id="9dcfb-159">A managed delegate is marshaled as a COM interface or as a function pointer, based on the calling mechanism:</span></span>  
  
-   <span data-ttu-id="9dcfb-160">Para a invocação de plataforma, um representante tem o marshaling realizado como um ponteiro de função não gerenciada, por padrão.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-160">For platform invoke, a delegate is marshaled as an unmanaged function pointer by default.</span></span>  
  
-   <span data-ttu-id="9dcfb-161">Para a interoperabilidade COM, um representante tem o marshaling realizado como uma interface COM do tipo **_Delegate**, por padrão.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-161">For COM interop, a delegate is marshaled as a COM interface of type **_Delegate** by default.</span></span> <span data-ttu-id="9dcfb-162">A interface **_Delegate** é definida na biblioteca de tipos Mscorlib.tlb e contém o método <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType>, que permite chamar o método referenciado pelo representante.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-162">The **_Delegate** interface is defined in the Mscorlib.tlb type library and contains the <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> method, which enables you to call the method that the delegate references.</span></span>  
  
 <span data-ttu-id="9dcfb-163">A tabela a seguir mostra as opções de marshaling para o tipo de dados do representante gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-163">The following table shows the marshaling options for the managed delegate data type.</span></span> <span data-ttu-id="9dcfb-164">O atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute> fornece vários valores de enumeração <xref:System.Runtime.InteropServices.UnmanagedType> para realizar marshaling de representantes.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-164">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal delegates.</span></span>  
  
|<span data-ttu-id="9dcfb-165">Tipo de enumeração</span><span class="sxs-lookup"><span data-stu-id="9dcfb-165">Enumeration type</span></span>|<span data-ttu-id="9dcfb-166">Descrição do formato não gerenciado</span><span class="sxs-lookup"><span data-stu-id="9dcfb-166">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="9dcfb-167">**UnmanagedType.FunctionPtr**</span><span class="sxs-lookup"><span data-stu-id="9dcfb-167">**UnmanagedType.FunctionPtr**</span></span>|<span data-ttu-id="9dcfb-168">Um ponteiro de função não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-168">An unmanaged function pointer.</span></span>|  
|<span data-ttu-id="9dcfb-169">**UnmanagedType.Interface**</span><span class="sxs-lookup"><span data-stu-id="9dcfb-169">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="9dcfb-170">Uma interface do tipo **_Delegate**, conforme definido em Mscorlib.tlb.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-170">An interface of type **_Delegate**, as defined in Mscorlib.tlb.</span></span>|  
  
 <span data-ttu-id="9dcfb-171">Considere o código de exemplo a seguir, no qual os métodos da `DelegateTestInterface` são exportados para uma biblioteca de tipos COM.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-171">Consider the following example code in which the methods of `DelegateTestInterface` are exported to a COM type library.</span></span> <span data-ttu-id="9dcfb-172">Observe que apenas os representantes marcados com a palavra-chave **ref** (ou **ByRef**) são passados como parâmetros de Entrada/Saída.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-172">Notice that only delegates marked with the **ref** (or **ByRef**) keyword are passed as In/Out parameters.</span></span>  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
  
public interface DelegateTest {  
void m1(Delegate d);  
void m2([MarshalAs(UnmanagedType.Interface)] Delegate d);     
void m3([MarshalAs(UnmanagedType.Interface)] ref Delegate d);    
void m4([MarshalAs(UnmanagedType.FunctionPtr)] Delegate d);   
void m5([MarshalAs(UnmanagedType.FunctionPtr)] ref Delegate d);     
}  
```  
  
### <a name="type-library-representation"></a><span data-ttu-id="9dcfb-173">Representação da biblioteca de tipos</span><span class="sxs-lookup"><span data-stu-id="9dcfb-173">Type library representation</span></span>  
  
```  
importlib("mscorlib.tlb");  
interface DelegateTest : IDispatch {  
[id(…)] HRESULT m1([in] _Delegate* d);  
[id(…)] HRESULT m2([in] _Delegate* d);  
[id(…)] HRESULT m3([in, out] _Delegate** d);  
[id()] HRESULT m4([in] int d);  
[id()] HRESULT m5([in, out] int *d);  
   };  
```  
  
 <span data-ttu-id="9dcfb-174">Um ponteiro de função pode ser desreferenciado, assim como qualquer outro ponteiro de função não gerenciada pode ser desreferenciado.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-174">A function pointer can be dereferenced, just as any other unmanaged function pointer can be dereferenced.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9dcfb-175">Uma referência ao ponteiro de função para um representante gerenciado mantido por um código não gerenciado não impede o Common Language Runtime de executar a coleta de lixo no objeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-175">A reference to the function pointer to a managed delegate held by unmanaged code does not prevent the common language runtime from performing garbage collection on the managed object.</span></span>  
  
 <span data-ttu-id="9dcfb-176">Por exemplo, o código a seguir está incorreto porque a referência ao objeto `cb`, passado para o método `SetChangeHandler`, não mantém `cb` ativo além da vida útil do método `Test`.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-176">For example, the following code is incorrect because the reference to the `cb` object, passed to the `SetChangeHandler` method, does not keep `cb` alive beyond the life of the `Test` method.</span></span> <span data-ttu-id="9dcfb-177">Depois que o objeto `cb` é coletado como lixo, o ponteiro de função passado para `SetChangeHandler` não é mais válido.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-177">Once the `cb` object is garbage collected, the function pointer passed to `SetChangeHandler` is no longer valid.</span></span>  
  
```csharp  
public class ExternalAPI {  
   [DllImport("External.dll")]  
   public static extern void SetChangeHandler(  
      [MarshalAs(UnmanagedType.FunctionPtr)]ChangeDelegate d);  
}  
public delegate bool ChangeDelegate([MarshalAs(UnmanagedType.LPWStr) string S);  
public class CallBackClass {  
   public bool OnChange(string S){ return true;}  
}  
internal class DelegateTest {  
   public static void Test() {  
      CallBackClass cb = new CallBackClass();  
      // Caution: The following reference on the cb object does not keep the   
      // object from being garbage collected after the Main method   
      // executes.  
      ExternalAPI.SetChangeHandler(new ChangeDelegate(cb.OnChange));     
   }  
}  
```  
  
 <span data-ttu-id="9dcfb-178">Para compensar a coleta de lixo inesperada, o chamador deve garantir que o objeto `cb` é mantido ativo enquanto o ponteiro de função não gerenciada está em uso.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-178">To compensate for unexpected garbage collection, the caller must ensure that the `cb` object is kept alive as long as the unmanaged function pointer is in use.</span></span> <span data-ttu-id="9dcfb-179">Opcionalmente, você pode fazer com que o código não gerenciado notifique o código gerenciado quando o ponteiro de função não é mais necessário, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-179">Optionally, you can have the unmanaged code notify the managed code when the function pointer is no longer needed, as the following example shows.</span></span>  
  
```csharp  
internal class DelegateTest {  
   CallBackClass cb;  
   // Called before ever using the callback function.  
   public static void SetChangeHandler() {  
      cb = new CallBackClass();  
      ExternalAPI.SetChangeHandler(new ChangeDelegate(cb.OnChange));  
   }  
   // Called after using the callback function for the last time.  
   public static void RemoveChangeHandler() {  
      // The cb object can be collected now. The unmanaged code is   
      // finished with the callback function.  
      cb = null;  
   }  
}  
```  
  
## <a name="default-marshaling-for-value-types"></a><span data-ttu-id="9dcfb-180">Marshaling padrão para tipos de valor</span><span class="sxs-lookup"><span data-stu-id="9dcfb-180">Default marshaling for value types</span></span>  
 <span data-ttu-id="9dcfb-181">A maioria dos tipos de valor, como inteiros e números de ponto flutuante, é [blittable](blittable-and-non-blittable-types.md) e não exige marshaling.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-181">Most value types, such as integers and floating-point numbers, are [blittable](blittable-and-non-blittable-types.md) and do not require marshaling.</span></span> <span data-ttu-id="9dcfb-182">Outros tipos [não blittable](blittable-and-non-blittable-types.md) têm diferentes representações na memória gerenciada e não gerenciada e exigem marshaling.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-182">Other [non-blittable](blittable-and-non-blittable-types.md) types have dissimilar representations in managed and unmanaged memory and do require marshaling.</span></span> <span data-ttu-id="9dcfb-183">Além disso, outros tipos de exigem a formatação explícita no limite de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-183">Still other types require explicit formatting across the interoperation boundary.</span></span>  
  
 <span data-ttu-id="9dcfb-184">Este tópico fornece as seguintes informações sobre tipos de valor formatados:</span><span class="sxs-lookup"><span data-stu-id="9dcfb-184">This topic provides the follow information on formatted value types:</span></span>  
  
-   [<span data-ttu-id="9dcfb-185">Tipos de valor usados na invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="9dcfb-185">Value Types Used in Platform Invoke</span></span>](#cpcondefaultmarshalingforvaluetypesanchor2)  
  
-   [<span data-ttu-id="9dcfb-186">Tipos de valor usados na interoperabilidade COM</span><span class="sxs-lookup"><span data-stu-id="9dcfb-186">Value Types Used in COM Interop</span></span>](#cpcondefaultmarshalingforvaluetypesanchor3)  
  
 <span data-ttu-id="9dcfb-187">Além de descrever os tipos formatados, este tópico identifica os [tipos de valor do sistema](#cpcondefaultmarshalingforvaluetypesanchor1) que têm um comportamento de marshaling incomum.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-187">In addition to describing formatted types, this topic identifies [System Value Types](#cpcondefaultmarshalingforvaluetypesanchor1) that have unusual marshaling behavior.</span></span>  
  
 <span data-ttu-id="9dcfb-188">Um tipo formatado é um tipo complexo que contém informações que controlam explicitamente o layout de seus membros na memória.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-188">A formatted type is a complex type that contains information that explicitly controls the layout of its members in memory.</span></span> <span data-ttu-id="9dcfb-189">As informações de layout de membro são fornecidas usando o atributo <xref:System.Runtime.InteropServices.StructLayoutAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-189">The member layout information is provided using the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="9dcfb-190">O layout pode ser um dos seguintes valores de enumeração <xref:System.Runtime.InteropServices.LayoutKind>:</span><span class="sxs-lookup"><span data-stu-id="9dcfb-190">The layout can be one of the following <xref:System.Runtime.InteropServices.LayoutKind> enumeration values:</span></span>  
  
-   <span data-ttu-id="9dcfb-191">**LayoutKind.Automatic**</span><span class="sxs-lookup"><span data-stu-id="9dcfb-191">**LayoutKind.Automatic**</span></span>  
  
     <span data-ttu-id="9dcfb-192">Indica que o Common Language Runtime está livre para reordenar os membros do tipo para eficiência.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-192">Indicates that the common language runtime is free to reorder the members of the type for efficiency.</span></span> <span data-ttu-id="9dcfb-193">No entanto, quando um tipo de valor é passado para um código não gerenciado, o layout dos membros é previsível.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-193">However, when a value type is passed to unmanaged code, the layout of the members is predictable.</span></span> <span data-ttu-id="9dcfb-194">Uma tentativa de realizar marshaling de uma estrutura como essa causa uma exceção automaticamente.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-194">An attempt to marshal such a structure automatically causes an exception.</span></span>  
  
-   <span data-ttu-id="9dcfb-195">**LayoutKind.Sequential**</span><span class="sxs-lookup"><span data-stu-id="9dcfb-195">**LayoutKind.Sequential**</span></span>  
  
     <span data-ttu-id="9dcfb-196">Indica que os membros do tipo devem ser dispostos na memória não gerenciada na mesma ordem em que aparecem na definição de tipo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-196">Indicates that the members of the type are to be laid out in unmanaged memory in the same order in which they appear in the managed type definition.</span></span>  
  
-   <span data-ttu-id="9dcfb-197">**LayoutKind.Explicit**</span><span class="sxs-lookup"><span data-stu-id="9dcfb-197">**LayoutKind.Explicit**</span></span>  
  
     <span data-ttu-id="9dcfb-198">Indica que os membros são dispostos de acordo com o <xref:System.Runtime.InteropServices.FieldOffsetAttribute> fornecido com cada campo.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-198">Indicates that the members are laid out according to the <xref:System.Runtime.InteropServices.FieldOffsetAttribute> supplied with each field.</span></span>  
  
<a name="cpcondefaultmarshalingforvaluetypesanchor2"></a>   
### <a name="value-types-used-in-platform-invoke"></a><span data-ttu-id="9dcfb-199">Tipos de valor usados na invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="9dcfb-199">Value Types Used in Platform Invoke</span></span>  
 <span data-ttu-id="9dcfb-200">No exemplo a seguir, os tipos `Point` e `Rect` fornecem informações de layout de membro usando o **StructLayoutAttribute**.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-200">In the following example the `Point` and `Rect` types provide member layout information using the **StructLayoutAttribute**.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
<StructLayout(LayoutKind.Sequential)> Public Structure Point  
   Public x As Integer  
   Public y As Integer  
End Structure  
<StructLayout(LayoutKind.Explicit)> Public Structure Rect  
   <FieldOffset(0)> Public left As Integer  
   <FieldOffset(4)> Public top As Integer  
   <FieldOffset(8)> Public right As Integer  
   <FieldOffset(12)> Public bottom As Integer  
End Structure  
```  
  
```csharp  
using System.Runtime.InteropServices;  
[StructLayout(LayoutKind.Sequential)]  
public struct Point {  
   public int x;  
   public int y;  
}     
  
[StructLayout(LayoutKind.Explicit)]  
public struct Rect {  
   [FieldOffset(0)] public int left;  
   [FieldOffset(4)] public int top;  
   [FieldOffset(8)] public int right;  
   [FieldOffset(12)] public int bottom;  
}  
```  
  
 <span data-ttu-id="9dcfb-201">Ao ter o marshaling realizado para um código não gerenciado, esses tipos formatados têm o marshaling realizado como estruturas C-style.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-201">When marshaled to unmanaged code, these formatted types are marshaled as C-style structures.</span></span> <span data-ttu-id="9dcfb-202">Isso fornece uma maneira fácil de chamar uma API não gerenciada que tem argumentos de estrutura.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-202">This provides an easy way of calling an unmanaged API that has structure arguments.</span></span> <span data-ttu-id="9dcfb-203">Por exemplo, as estruturas `POINT` e `RECT` podem ser passadas para a função **PtInRect** da API do Microsoft Win32 da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="9dcfb-203">For example, the `POINT` and `RECT` structures can be passed to the Microsoft Win32 API **PtInRect** function as follows:</span></span>  
  
```  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="9dcfb-204">Passe estruturas usando a seguinte definição de invocação de plataforma:</span><span class="sxs-lookup"><span data-stu-id="9dcfb-204">You can pass structures using the following platform invoke definition:</span></span>  
  
```vb  
Class Win32API      
   Declare Auto Function PtInRect Lib "User32.dll" _  
    (ByRef r As Rect, p As Point) As Boolean  
End Class  
```  
  
```csharp  
class Win32API {  
   [DllImport("User32.dll")]  
   public static extern Bool PtInRect(ref Rect r, Point p);  
}  
```  
  
 <span data-ttu-id="9dcfb-205">O tipo de valor `Rect` deve ser passado por referência porque a API não gerenciada está esperando que um ponteiro para um `RECT` seja passado para a função.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-205">The `Rect` value type must be passed by reference because the unmanaged API is expecting a pointer to a `RECT` to be passed to the function.</span></span> <span data-ttu-id="9dcfb-206">O tipo de valor `Point` é passado por valor porque a API não gerenciada espera que `POINT` seja passado na pilha.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-206">The `Point` value type is passed by value because the unmanaged API expects the `POINT` to be passed on the stack.</span></span> <span data-ttu-id="9dcfb-207">Essa diferença sutil é muito importante.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-207">This subtle difference is very important.</span></span> <span data-ttu-id="9dcfb-208">As referências são passadas para um código não gerenciado como ponteiros.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-208">References are passed to unmanaged code as pointers.</span></span> <span data-ttu-id="9dcfb-209">Os valores são passados para um código não gerenciado na pilha.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-209">Values are passed to unmanaged code on the stack.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9dcfb-210">Quando um tipo formatado tem o marshaling realizado como uma estrutura, apenas os campos no tipo são acessíveis.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-210">When a formatted type is marshaled as a structure, only the fields within the type are accessible.</span></span> <span data-ttu-id="9dcfb-211">Se o tipo tiver métodos, propriedades ou eventos, eles poderão ser acessados por meio do código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-211">If the type has methods, properties, or events, they are inaccessible from unmanaged code.</span></span>  
  
 <span data-ttu-id="9dcfb-212">As classes também podem ter o marshaling realizado para um código não gerenciado como estruturas C-style, desde que tenham um layout de membro fixo.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-212">Classes can also be marshaled to unmanaged code as C-style structures, provided they have fixed member layout.</span></span> <span data-ttu-id="9dcfb-213">As informações de layout de membro de uma classe também são fornecidas com o atributo <xref:System.Runtime.InteropServices.StructLayoutAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-213">The member layout information for a class is also provided with the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="9dcfb-214">A principal diferença entre os tipos de valor com layout fixo e classes com layout fixo é a maneira na qual eles tem o marshaling realizado para um código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-214">The main difference between value types with fixed layout and classes with fixed layout is the way in which they are marshaled to unmanaged code.</span></span> <span data-ttu-id="9dcfb-215">Os tipos de valor são passados por valor (na pilha) e, consequentemente, as alterações feitas nos membros do tipo pelo receptor não são vistas pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-215">Value types are passed by value (on the stack) and consequently any changes made to the members of the type by the callee are not seen by the caller.</span></span> <span data-ttu-id="9dcfb-216">Os tipos de referência são passados por referência (uma referência ao tipo é passada na pilha); consequentemente, todas as alterações feitas nos membros do tipo blittable de um tipo pelo receptor são vistas pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-216">Reference types are passed by reference (a reference to the type is passed on the stack); consequently, all changes made to blittable-type members of a type by the callee are seen by the caller.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9dcfb-217">Se um tipo de referência tiver membros de tipos não blittable, a conversão será necessária duas vezes: na primeira vez, em que um argumento é passado para o lado não gerenciado e, na segunda, após o retorno da chamada.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-217">If a reference type has members of non-blittable types, conversion is required twice: the first time when an argument is passed to the unmanaged side and the second time on return from the call.</span></span> <span data-ttu-id="9dcfb-218">Devido a essa sobrecarga agregada, os parâmetros de Entrada/Saída devem ser aplicados explicitamente a um argumento se o chamador deseja ver as alterações feitas pelo receptor.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-218">Due to this added overhead, In/Out parameters must be explicitly applied to an argument if the caller wants to see changes made by the callee.</span></span>  
  
 <span data-ttu-id="9dcfb-219">No exemplo a seguir, a classe `SystemTime` tem um layout de membro sequencial e pode ser passada para a função **GetSystemTime** da API do Win32.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-219">In the following example, the `SystemTime` class has sequential member layout and can be passed to the Win32 API **GetSystemTime** function.</span></span>  
  
```vb  
<StructLayout(LayoutKind.Sequential)> Public Class SystemTime  
   Public wYear As System.UInt16  
   Public wMonth As System.UInt16  
   Public wDayOfWeek As System.UInt16  
   Public wDay As System.UInt16  
   Public wHour As System.UInt16  
   Public wMinute As System.UInt16  
   Public wSecond As System.UInt16  
   Public wMilliseconds As System.UInt16  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
   public class SystemTime {  
   public ushort wYear;   
   public ushort wMonth;  
   public ushort wDayOfWeek;   
   public ushort wDay;   
   public ushort wHour;   
   public ushort wMinute;   
   public ushort wSecond;   
   public ushort wMilliseconds;   
}  
```  
  
 <span data-ttu-id="9dcfb-220">A função **GetSystemTime** é definida da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="9dcfb-220">The **GetSystemTime** function is defined as follows:</span></span>  
  
```  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="9dcfb-221">A definição equivalente de invocação de plataforma para **GetSystemTime** é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="9dcfb-221">The equivalent platform invoke definition for **GetSystemTime** is as follows:</span></span>  
  
```vb  
Public Class Win32  
   Declare Auto Sub GetSystemTime Lib "Kernel32.dll" (ByVal sysTime _  
   As SystemTime)  
End Class  
```  
  
```csharp  
class Win32API {  
   [DllImport("Kernel32.dll", CharSet=CharSet.Auto)]  
   public static extern void GetSystemTime(SystemTime st);  
}  
```  
  
 <span data-ttu-id="9dcfb-222">Observe que o argumento `SystemTime` não é digitado como um argumento de referência porque `SystemTime` é uma classe, não um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-222">Notice that the `SystemTime` argument is not typed as a reference argument because `SystemTime` is a class, not a value type.</span></span> <span data-ttu-id="9dcfb-223">Ao contrário dos tipos de valor, as classes são sempre passadas por referência.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-223">Unlike value types, classes are always passed by reference.</span></span>  
  
 <span data-ttu-id="9dcfb-224">O exemplo de código a seguir mostra outra classe `Point` que tem um método chamado `SetXY`.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-224">The following code example shows a different `Point` class that has a method called `SetXY`.</span></span> <span data-ttu-id="9dcfb-225">Como o tipo tem um layout sequencial, ele pode ser passado para um código não gerenciado e ter o marshaling realizado como uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-225">Because the type has sequential layout, it can be passed to unmanaged code and marshaled as a structure.</span></span> <span data-ttu-id="9dcfb-226">No entanto, o membro `SetXY` não pode ser chamado em um código não gerenciado, mesmo que o objeto seja passado por referência.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-226">However, the `SetXY` member is not callable from unmanaged code, even though the object is passed by reference.</span></span>  
  
```vb  
<StructLayout(LayoutKind.Sequential)> Public Class Point  
   Private x, y As Integer  
   Public Sub SetXY(x As Integer, y As Integer)  
      Me.x = x  
      Me.y = y  
   End Sub  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public class Point {  
   int x, y;  
   public void SetXY(int x, int y){   
      this.x = x;  
      this.y = y;  
   }  
}  
```  
  
<a name="cpcondefaultmarshalingforvaluetypesanchor3"></a>   
### <a name="value-types-used-in-com-interop"></a><span data-ttu-id="9dcfb-227">Tipos de valor usados na interoperabilidade COM</span><span class="sxs-lookup"><span data-stu-id="9dcfb-227">Value Types Used in COM Interop</span></span>  
 <span data-ttu-id="9dcfb-228">Os tipos formatados também podem ser passados para chamadas de método da interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-228">Formatted types can also be passed to COM interop method calls.</span></span> <span data-ttu-id="9dcfb-229">Na verdade, quando exportados para uma biblioteca de tipos, os tipos de valor são convertidos em estruturas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-229">In fact, when exported to a type library, value types are automatically converted to structures.</span></span> <span data-ttu-id="9dcfb-230">Como mostra o exemplo a seguir, o tipo de valor `Point` se torna uma definição de tipo (typedef) com o nome `Point`.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-230">As the following example shows, the `Point` value type becomes a type definition (typedef) with the name `Point`.</span></span> <span data-ttu-id="9dcfb-231">Todas as referências ao tipo de valor `Point` em outros lugares da biblioteca de tipos são substituídas pela typedef `Point`.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-231">All references to the `Point` value type elsewhere in the type library are replaced with the `Point` typedef.</span></span>  
  
 <span data-ttu-id="9dcfb-232">**Representação da biblioteca de tipos**</span><span class="sxs-lookup"><span data-stu-id="9dcfb-232">**Type library representation**</span></span>  
  
```  
typedef struct tagPoint {  
   int x;  
   int y;  
} Point;  
interface _Graphics {  
   …  
   HRESULT SetPoint ([in] Point p)  
   HRESULT SetPointRef ([in,out] Point *p)  
   HRESULT GetPoint ([out,retval] Point *p)  
}  
```  
  
 <span data-ttu-id="9dcfb-233">As mesmas regras usadas para realizar marshaling de valores e de referências para chamadas de invocação de plataforma são usadas durante o marshaling por meio de interfaces COM.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-233">The same rules used to marshal values and references to platform invoke calls are used when marshaling through COM interfaces.</span></span> <span data-ttu-id="9dcfb-234">Por exemplo, quando uma instância do tipo de valor `Point` é passada do .NET Framework para o COM, o `Point` é passado por valor.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-234">For example, when an instance of the `Point` value type is passed from the .NET Framework to COM, the `Point` is passed by value.</span></span> <span data-ttu-id="9dcfb-235">Se o tipo de valor `Point` é passado por referência, um ponteiro para um `Point` é passado na pilha.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-235">If the `Point` value type is passed by reference, a pointer to a `Point` is passed on the stack.</span></span> <span data-ttu-id="9dcfb-236">O marshaler de interoperabilidade não dá suporte a níveis mais altos de indireção (**Ponto** \*\*) em qualquer direção.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-236">The interop marshaler does not support higher levels of indirection (**Point** \*\*) in either direction.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9dcfb-237">Estruturas que têm o valor de enumeração <xref:System.Runtime.InteropServices.LayoutKind> definido como **Explicit** não podem ser usadas na interoperabilidade COM porque a biblioteca de tipos exportada não pode expressar um layout explícito.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-237">Structures having the <xref:System.Runtime.InteropServices.LayoutKind> enumeration value set to **Explicit** cannot be used in COM interop because the exported type library cannot express an explicit layout.</span></span>  
  
<a name="cpcondefaultmarshalingforvaluetypesanchor1"></a>   
### <a name="system-value-types"></a><span data-ttu-id="9dcfb-238">Tipos de valor do sistema</span><span class="sxs-lookup"><span data-stu-id="9dcfb-238">System Value Types</span></span>  
 <span data-ttu-id="9dcfb-239">O namespace <xref:System> tem vários tipos de valor que representam o formato demarcado dos tipos primitivos de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-239">The <xref:System> namespace has several value types that represent the boxed form of the runtime primitive types.</span></span> <span data-ttu-id="9dcfb-240">Por exemplo, a estrutura <xref:System.Int32?displayProperty=nameWithType> do tipo de valor representa o formato demarcado de **ELEMENT_TYPE_I4**.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-240">For example, the value type <xref:System.Int32?displayProperty=nameWithType> structure represents the boxed form of **ELEMENT_TYPE_I4**.</span></span> <span data-ttu-id="9dcfb-241">Em vez de realizar marshaling desses tipos como estruturas, assim como ocorre com outros tipos formatados, realize marshaling deles da mesma maneira como os tipos primitivos demarcados por eles.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-241">Instead of marshaling these types as structures, as other formatted types are, you marshal them in the same way as the primitive types they box.</span></span> <span data-ttu-id="9dcfb-242">Portanto, **System.Int32** tem o marshaling realizado como **ELEMENT_TYPE_I4**, em vez de como uma estrutura que contém um único membro do tipo **long**.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-242">**System.Int32** is therefore marshaled as **ELEMENT_TYPE_I4** instead of as a structure containing a single member of type **long**.</span></span> <span data-ttu-id="9dcfb-243">A tabela a seguir contém uma lista dos tipos de valor no namespace **System** que são representações demarcadas de tipos primitivos.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-243">The following table contains a list of the value types in the **System** namespace that are boxed representations of primitive types.</span></span>  
  
|<span data-ttu-id="9dcfb-244">Tipo de valor do sistema</span><span class="sxs-lookup"><span data-stu-id="9dcfb-244">System value type</span></span>|<span data-ttu-id="9dcfb-245">Tipo de elemento</span><span class="sxs-lookup"><span data-stu-id="9dcfb-245">Element type</span></span>|  
|-----------------------|------------------|  
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="9dcfb-246">**ELEMENT_TYPE_BOOLEAN**</span><span class="sxs-lookup"><span data-stu-id="9dcfb-246">**ELEMENT_TYPE_BOOLEAN**</span></span>|  
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="9dcfb-247">**ELEMENT_TYPE_I1**</span><span class="sxs-lookup"><span data-stu-id="9dcfb-247">**ELEMENT_TYPE_I1**</span></span>|  
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="9dcfb-248">**ELEMENT_TYPE_UI1**</span><span class="sxs-lookup"><span data-stu-id="9dcfb-248">**ELEMENT_TYPE_UI1**</span></span>|  
|<xref:System.Char?displayProperty=nameWithType>|<span data-ttu-id="9dcfb-249">**ELEMENT_TYPE_CHAR**</span><span class="sxs-lookup"><span data-stu-id="9dcfb-249">**ELEMENT_TYPE_CHAR**</span></span>|  
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="9dcfb-250">**ELEMENT_TYPE_I2**</span><span class="sxs-lookup"><span data-stu-id="9dcfb-250">**ELEMENT_TYPE_I2**</span></span>|  
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="9dcfb-251">**ELEMENT_TYPE_U2**</span><span class="sxs-lookup"><span data-stu-id="9dcfb-251">**ELEMENT_TYPE_U2**</span></span>|  
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="9dcfb-252">**ELEMENT_TYPE_I4**</span><span class="sxs-lookup"><span data-stu-id="9dcfb-252">**ELEMENT_TYPE_I4**</span></span>|  
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="9dcfb-253">**ELEMENT_TYPE_U4**</span><span class="sxs-lookup"><span data-stu-id="9dcfb-253">**ELEMENT_TYPE_U4**</span></span>|  
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="9dcfb-254">**ELEMENT_TYPE_I8**</span><span class="sxs-lookup"><span data-stu-id="9dcfb-254">**ELEMENT_TYPE_I8**</span></span>|  
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="9dcfb-255">**ELEMENT_TYPE_U8**</span><span class="sxs-lookup"><span data-stu-id="9dcfb-255">**ELEMENT_TYPE_U8**</span></span>|  
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="9dcfb-256">**ELEMENT_TYPE_R4**</span><span class="sxs-lookup"><span data-stu-id="9dcfb-256">**ELEMENT_TYPE_R4**</span></span>|  
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="9dcfb-257">**ELEMENT_TYPE_R8**</span><span class="sxs-lookup"><span data-stu-id="9dcfb-257">**ELEMENT_TYPE_R8**</span></span>|  
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="9dcfb-258">**ELEMENT_TYPE_STRING**</span><span class="sxs-lookup"><span data-stu-id="9dcfb-258">**ELEMENT_TYPE_STRING**</span></span>|  
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="9dcfb-259">**ELEMENT_TYPE_I**</span><span class="sxs-lookup"><span data-stu-id="9dcfb-259">**ELEMENT_TYPE_I**</span></span>|  
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="9dcfb-260">**ELEMENT_TYPE_U**</span><span class="sxs-lookup"><span data-stu-id="9dcfb-260">**ELEMENT_TYPE_U**</span></span>|  
  
 <span data-ttu-id="9dcfb-261">Alguns outros tipos de valor no namespace **System** são manipulados de maneira diferente.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-261">Some other value types in the **System** namespace are handled differently.</span></span> <span data-ttu-id="9dcfb-262">Como o código não gerenciado já tem formatos bem estabelecidos para esses tipos, o marshaler tem regras especiais para realizar marshaling deles.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-262">Because the unmanaged code already has well-established formats for these types, the marshaler has special rules for marshaling them.</span></span> <span data-ttu-id="9dcfb-263">A tabela a seguir lista os tipos de valor especiais no namespace **System**, bem como o tipo não gerenciado para o qual eles tem o marshaling realizado.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-263">The following table lists the special value types in the **System** namespace, as well as the unmanaged type they are marshaled to.</span></span>  
  
|<span data-ttu-id="9dcfb-264">Tipo de valor do sistema</span><span class="sxs-lookup"><span data-stu-id="9dcfb-264">System value type</span></span>|<span data-ttu-id="9dcfb-265">Tipo de IDL</span><span class="sxs-lookup"><span data-stu-id="9dcfb-265">IDL type</span></span>|  
|-----------------------|--------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="9dcfb-266">**DATE**</span><span class="sxs-lookup"><span data-stu-id="9dcfb-266">**DATE**</span></span>|  
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="9dcfb-267">**DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="9dcfb-267">**DECIMAL**</span></span>|  
|<xref:System.Guid?displayProperty=nameWithType>|<span data-ttu-id="9dcfb-268">**GUID**</span><span class="sxs-lookup"><span data-stu-id="9dcfb-268">**GUID**</span></span>|  
|<xref:System.Drawing.Color?displayProperty=nameWithType>|<span data-ttu-id="9dcfb-269">**OLE_COLOR**</span><span class="sxs-lookup"><span data-stu-id="9dcfb-269">**OLE_COLOR**</span></span>|  
  
 <span data-ttu-id="9dcfb-270">O código a seguir mostra a definição dos tipos não gerenciados **DATE**, **GUID**, **DECIMAL** e **OLE_COLOR** na biblioteca de tipos Stdole2.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-270">The following code shows the definition of the unmanaged types **DATE**, **GUID**, **DECIMAL**, and **OLE_COLOR** in the Stdole2 type library.</span></span>  
  
#### <a name="type-library-representation"></a><span data-ttu-id="9dcfb-271">Representação da biblioteca de tipos</span><span class="sxs-lookup"><span data-stu-id="9dcfb-271">Type library representation</span></span>  
  
```  
typedef double DATE;  
typedef DWORD OLE_COLOR;  
  
typedef struct tagDEC {  
    USHORT    wReserved;  
    BYTE      scale;  
    BYTE      sign;  
    ULONG     Hi32;  
    ULONGLONG Lo64;  
} DECIMAL;  
  
typedef struct tagGUID {  
    DWORD Data1;  
    WORD  Data2;  
    WORD  Data3;  
    BYTE  Data4[ 8 ];  
} GUID;  
```  
  
 <span data-ttu-id="9dcfb-272">O código a seguir mostra as definições correspondentes na interface `IValueTypes` gerenciada.</span><span class="sxs-lookup"><span data-stu-id="9dcfb-272">The following code shows the corresponding definitions in the managed `IValueTypes` interface.</span></span>  
  
```vb  
Public Interface IValueTypes  
   Sub M1(d As System.DateTime)  
   Sub M2(d As System.Guid)  
   Sub M3(d As System.Decimal)  
   Sub M4(d As System.Drawing.Color)  
End Interface  
```  
  
```csharp  
public interface IValueTypes {  
   void M1(System.DateTime d);  
   void M2(System.Guid d);  
   void M3(System.Decimal d);  
   void M4(System.Drawing.Color d);  
}  
```  
  
#### <a name="type-library-representation"></a><span data-ttu-id="9dcfb-273">Representação da biblioteca de tipos</span><span class="sxs-lookup"><span data-stu-id="9dcfb-273">Type library representation</span></span>  
  
```  
[…]  
interface IValueTypes : IDispatch {  
   HRESULT M1([in] DATE d);  
   HRESULT M2([in] GUID d);  
   HRESULT M3([in] DECIMAL d);  
   HRESULT M4([in] OLE_COLOR d);  
};  
```  
  
## <a name="see-also"></a><span data-ttu-id="9dcfb-274">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9dcfb-274">See Also</span></span>  
 [<span data-ttu-id="9dcfb-275">Tipos blittable e não blittable</span><span class="sxs-lookup"><span data-stu-id="9dcfb-275">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)  
 [<span data-ttu-id="9dcfb-276">Copiando e fixando</span><span class="sxs-lookup"><span data-stu-id="9dcfb-276">Copying and Pinning</span></span>](copying-and-pinning.md)  
 [<span data-ttu-id="9dcfb-277">Marshaling padrão para matrizes</span><span class="sxs-lookup"><span data-stu-id="9dcfb-277">Default Marshaling for Arrays</span></span>](default-marshaling-for-arrays.md)  
 [<span data-ttu-id="9dcfb-278">Marshaling padrão para objetos</span><span class="sxs-lookup"><span data-stu-id="9dcfb-278">Default Marshaling for Objects</span></span>](default-marshaling-for-objects.md)  
 [<span data-ttu-id="9dcfb-279">Marshaling padrão para cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="9dcfb-279">Default Marshaling for Strings</span></span>](default-marshaling-for-strings.md)
