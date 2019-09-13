---
title: APIs que dependem de reflexão
ms.date: 03/30/2017
ms.assetid: f9532629-6594-4a41-909f-d083f30a42f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ba60b6d97d1441cefc9392067c797504f454ac59
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894523"
---
# <a name="apis-that-rely-on-reflection"></a><span data-ttu-id="3d4bf-102">APIs que dependem de reflexão</span><span class="sxs-lookup"><span data-stu-id="3d4bf-102">APIs That Rely on Reflection</span></span>
<span data-ttu-id="3d4bf-103">Em alguns casos, o uso de reflexão no código não é óbvio e, portanto, a cadeia de ferramentas de .NET Native não preserva os metadados necessários no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3d4bf-103">In some cases, the use of reflection in code isn't obvious, and so the .NET Native tool chain doesn't preserve metadata that is needed at run time.</span></span> <span data-ttu-id="3d4bf-104">Este tópico abrange algumas APIs ou padrões de programação comuns que não são consideradas como parte da API de reflexão, mas que dependem de reflexão para serem executados com êxito.</span><span class="sxs-lookup"><span data-stu-id="3d4bf-104">This topic covers some common APIs or common programming patterns that aren't considered part of the reflection API but that rely on reflection to execute successfully.</span></span> <span data-ttu-id="3d4bf-105">Se você usá-los no código-fonte, poderá adicionar informações sobre eles no arquivo de diretivas de tempo de execução (.rd.xml), de modo que as chamadas a essas APIs não gerem uma exceção [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) ou outras exceções em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3d4bf-105">If you use them in your source code, you can add information about them to the runtime directives (.rd.xml) file so that calls to these APIs do not throw a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception or some other exception at run time.</span></span>  
  
## <a name="typemakegenerictype-method"></a><span data-ttu-id="3d4bf-106">Método Type.MakeGenericType</span><span class="sxs-lookup"><span data-stu-id="3d4bf-106">Type.MakeGenericType method</span></span>  
 <span data-ttu-id="3d4bf-107">Você pode instanciar dinamicamente um tipo genérico `AppClass<T>` chamando o método <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> usando um código da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="3d4bf-107">You can dynamically instantiate a generic type `AppClass<T>` by calling the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method by using code like this:</span></span>  
  
 [!code-csharp[ProjectN#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/type_makegenerictype1.cs#1)]  
  
 <span data-ttu-id="3d4bf-108">Para que esse código seja bem-sucedido no tempo de execução, vários itens de metadados são necessários.</span><span class="sxs-lookup"><span data-stu-id="3d4bf-108">For this code to succeed at run time, several items of metadata are required.</span></span> <span data-ttu-id="3d4bf-109">O primeiro é metadados `Browse` para o tipo genérico não instanciado, `AppClass<T>`:</span><span class="sxs-lookup"><span data-stu-id="3d4bf-109">The first is `Browse` metadata for the uninstantiated generic type, `AppClass<T>`:</span></span>  
  
```xml  
<Type Name="App1.AppClass`1" Browse="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="3d4bf-110">Isso permite que a chamada de método <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> seja bem-sucedida e retorne um objeto <xref:System.Type> válido.</span><span class="sxs-lookup"><span data-stu-id="3d4bf-110">This allows the <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> method call to succeed and return a valid <xref:System.Type> object.</span></span>  
  
 <span data-ttu-id="3d4bf-111">Mesmo quando você adiciona metadados ao tipo genérico não instanciado, uma chamada ao método <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> gera uma exceção [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md):</span><span class="sxs-lookup"><span data-stu-id="3d4bf-111">But even when you add metadata for the uninstantiated generic type, calling the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method throws a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception:</span></span>  
  
<span data-ttu-id="3d4bf-112">Esta operação não pode ser executada porque os metadados para o seguinte tipo foram removidos por motivos de desempenho:</span><span class="sxs-lookup"><span data-stu-id="3d4bf-112">This operation cannot be carried out as metadata for the following type was removed for performance reasons:</span></span>  
  
<span data-ttu-id="3d4bf-113">`App1.AppClass`1 < > System. Int32 '.</span><span class="sxs-lookup"><span data-stu-id="3d4bf-113">`App1.AppClass`1<System.Int32>\`.</span></span>  
  
 <span data-ttu-id="3d4bf-114">Você pode adicionar a seguinte diretiva de tempo de execução ao arquivo de diretivas de tempo de execução para adicionar metadados `Activate` à instanciação específica sobre `AppClass<T>` de <xref:System.Int32?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="3d4bf-114">You can add the following run-time directive to the runtime directives file to add `Activate` metadata for the specific instantiation over `AppClass<T>` of <xref:System.Int32?displayProperty=nameWithType>:</span></span>  
  
```xml  
<TypeInstantiation Name="App1.AppClass" Arguments="System.Int32"   
                   Activate="Required Public" />  
```  
  
 <span data-ttu-id="3d4bf-115">Cada instanciação diferente em `AppClass<T>` exigirá uma diretiva separada se estiver sendo criada com o método <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> e não for usada estaticamente.</span><span class="sxs-lookup"><span data-stu-id="3d4bf-115">Each different instantiation over `AppClass<T>` requires a separate directive if it is being created with the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method and not used statically.</span></span>  
  
## <a name="methodinfomakegenericmethod-method"></a><span data-ttu-id="3d4bf-116">Método MethodInfo.MakeGenericMethod</span><span class="sxs-lookup"><span data-stu-id="3d4bf-116">MethodInfo.MakeGenericMethod method</span></span>  
 <span data-ttu-id="3d4bf-117">Dada a classe `Class1` com um método genérico `GetMethod<T>(T t)`, `GetMethod` pode ser invocado por meio de reflexão usando um código da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="3d4bf-117">Given a class `Class1` with a generic method `GetMethod<T>(T t)`, `GetMethod` can be invoked through reflection by using code like this:</span></span>  
  
 [!code-csharp[ProjectN#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/makegenericmethod1.cs#2)]  
  
 <span data-ttu-id="3d4bf-118">Para ser executado com êxito, esse código requer vários itens de metadados:</span><span class="sxs-lookup"><span data-stu-id="3d4bf-118">To run successfully, this code requires several items of metadata:</span></span>  
  
- <span data-ttu-id="3d4bf-119">Metadados `Browse` para o tipo cujo método você deseja chamar.</span><span class="sxs-lookup"><span data-stu-id="3d4bf-119">`Browse` metadata for the type whose method you want to call.</span></span>  
  
- <span data-ttu-id="3d4bf-120">Metadados `Browse` para o método que você deseja chamar.</span><span class="sxs-lookup"><span data-stu-id="3d4bf-120">`Browse` metadata for the method you want to call.</span></span>  <span data-ttu-id="3d4bf-121">Se for um método público, adicionar metadados `Browse` públicos ao tipo recipiente também inclui o método.</span><span class="sxs-lookup"><span data-stu-id="3d4bf-121">If it is a public method, adding public `Browse` metadata for the containing type includes the method, too.</span></span>  
  
- <span data-ttu-id="3d4bf-122">Metadados dinâmicos para o método que você deseja chamar, de modo que o delegado de invocação de reflexão não seja removido pela cadeia de ferramentas de .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3d4bf-122">Dynamic metadata for the method you want to call, so that the reflection invocation delegate is not removed by the .NET Native tool chain.</span></span> <span data-ttu-id="3d4bf-123">Se os metadados dinâmicos não estiverem presentes para o método, a exceção a seguir é acionada quando o método <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> é chamado:</span><span class="sxs-lookup"><span data-stu-id="3d4bf-123">If dynamic metadata is missing for the method, the following exception is thrown when the <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> method is called:</span></span>  
  
    ```output
    MakeGenericMethod() cannot create this generic method instantiation because the instantiation was not metadata-enabled: 'App1.Class1.GenMethod<Int32>(Int32)'.  
    ```  
  
 <span data-ttu-id="3d4bf-124">As seguintes diretivas de tempo de execução garantem que todos os metadados estão disponíveis:</span><span class="sxs-lookup"><span data-stu-id="3d4bf-124">The following runtime directives ensure that all required metadata is available:</span></span>  
  
```xml  
<Type Name="App1.Class1" Browse="Required PublicAndInternal">  
   <MethodInstantiation Name="GenMethod" Arguments="System.Int32" Dynamic="Required"/>  
</Type>  
```  
  
 <span data-ttu-id="3d4bf-125">A diretiva `MethodInstantiation` é necessária para cada instanciação diferente do método é invocada dinamicamente, e o elemento `Arguments` é atualizado para refletir cada argumento de instanciação diferente.</span><span class="sxs-lookup"><span data-stu-id="3d4bf-125">A `MethodInstantiation` directive is required for each different instantiation of the method that is dynamically invoked, and the `Arguments` element is updated to reflect each different instantiation argument.</span></span>  
  
## <a name="arraycreateinstance-and-typemaketypearray-methods"></a><span data-ttu-id="3d4bf-126">Métodos Array.CreateInstance e Type.MakeTypeArray</span><span class="sxs-lookup"><span data-stu-id="3d4bf-126">Array.CreateInstance and Type.MakeTypeArray methods</span></span>  
 <span data-ttu-id="3d4bf-127">A exemplo a seguir chama os métodos <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> e <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> em um tipo `Class1`.</span><span class="sxs-lookup"><span data-stu-id="3d4bf-127">The following example calls the <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> methods on a type, `Class1`.</span></span>  
  
 [!code-csharp[ProjectN#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/array1.cs#3)]  
  
 <span data-ttu-id="3d4bf-128">Se não houver nenhum metadado matriz, é apresentado o seguinte erro:</span><span class="sxs-lookup"><span data-stu-id="3d4bf-128">If no array metadata is present, the following error results:</span></span>  
  
```output
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.Class1[]  
  
Unfortunately, no further information is available.  
```  
  
 <span data-ttu-id="3d4bf-129">Metadados `Browse` para o tipo de matriz são necessários para instanciá-lo dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="3d4bf-129">`Browse` metadata for the array type is required to dynamically instantiate it.</span></span>  <span data-ttu-id="3d4bf-130">A diretiva de tempo de execução a seguir permite a instanciação dinâmica do `Class1[]`.</span><span class="sxs-lookup"><span data-stu-id="3d4bf-130">The following runtime directive allows dynamic instantiation of `Class1[]`.</span></span>  
  
```xml  
<Type Name="App1.Class1[]" Browse="Required Public" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="3d4bf-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3d4bf-131">See also</span></span>

- [<span data-ttu-id="3d4bf-132">Introdução</span><span class="sxs-lookup"><span data-stu-id="3d4bf-132">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)
- [<span data-ttu-id="3d4bf-133">Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="3d4bf-133">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
