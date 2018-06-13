---
title: Reflexão (C#)
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: fc5c3f6af1a089d824289a55f6781e887b7cfc56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340431"
---
# <a name="reflection-c"></a><span data-ttu-id="a1890-102">Reflexão (C#)</span><span class="sxs-lookup"><span data-stu-id="a1890-102">Reflection (C#)</span></span>
<span data-ttu-id="a1890-103">A reflexão fornece objetos (do tipo <xref:System.Type>) que descrevem assemblies, módulos e tipos.</span><span class="sxs-lookup"><span data-stu-id="a1890-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="a1890-104">É possível usar a reflexão para criar dinamicamente uma instância de um tipo, associar o tipo a um objeto existente ou obter o tipo de um objeto existente e invocar seus métodos ou acessar suas propriedades e campos.</span><span class="sxs-lookup"><span data-stu-id="a1890-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="a1890-105">Se você estiver usando atributos em seu código, a reflexão permite acessá-los.</span><span class="sxs-lookup"><span data-stu-id="a1890-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="a1890-106">Para obter mais informações, consulte [Atributos](../../../../docs/standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="a1890-106">For more information, see [Attributes](../../../../docs/standard/attributes/index.md).</span></span>  
  
 <span data-ttu-id="a1890-107">Veja um exemplo simples de reflexão usando o método estático `GetType` – herdado por todos os tipos da classe base `Object` – para obter o tipo de uma variável:</span><span class="sxs-lookup"><span data-stu-id="a1890-107">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```csharp  
// Using GetType to obtain type information:  
int i = 42;  
System.Type type = i.GetType();  
System.Console.WriteLine(type);  
```  
  
 <span data-ttu-id="a1890-108">A saída é:</span><span class="sxs-lookup"><span data-stu-id="a1890-108">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="a1890-109">O exemplo a seguir usa a reflexão para obter o nome completo do assembly carregado.</span><span class="sxs-lookup"><span data-stu-id="a1890-109">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```csharp  
// Using Reflection to get information from an Assembly:  
System.Reflection.Assembly info = typeof(System.Int32).Assembly;  
System.Console.WriteLine(info);  
```  
  
 <span data-ttu-id="a1890-110">A saída é:</span><span class="sxs-lookup"><span data-stu-id="a1890-110">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
> [!NOTE]
>  <span data-ttu-id="a1890-111">As palavras-chave de C# `protected` e `internal` não têm significado no IL e não são usadas nas APIs de reflexão.</span><span class="sxs-lookup"><span data-stu-id="a1890-111">The C# keywords `protected` and `internal` have no meaning in IL and are not used in the reflection APIs.</span></span> <span data-ttu-id="a1890-112">Os termos correspondentes na IL são *Família* e *Assembly*.</span><span class="sxs-lookup"><span data-stu-id="a1890-112">The corresponding terms in IL are *Family* and *Assembly*.</span></span> <span data-ttu-id="a1890-113">Para identificar um método `internal` usando a reflexão, use a propriedade <xref:System.Reflection.MethodBase.IsAssembly%2A>.</span><span class="sxs-lookup"><span data-stu-id="a1890-113">To identify an `internal` method using reflection, use the <xref:System.Reflection.MethodBase.IsAssembly%2A> property.</span></span> <span data-ttu-id="a1890-114">Para identificar um método `protected internal`, use o <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span><span class="sxs-lookup"><span data-stu-id="a1890-114">To identify a `protected internal` method, use the <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span></span>  
  
## <a name="reflection-overview"></a><span data-ttu-id="a1890-115">Visão geral da reflexão</span><span class="sxs-lookup"><span data-stu-id="a1890-115">Reflection Overview</span></span>  
 <span data-ttu-id="a1890-116">A reflexão é útil nas seguintes situações:</span><span class="sxs-lookup"><span data-stu-id="a1890-116">Reflection is useful in the following situations:</span></span>  
  
-   <span data-ttu-id="a1890-117">Quando você precisa acessar atributos nos metadados do seu programa.</span><span class="sxs-lookup"><span data-stu-id="a1890-117">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="a1890-118">Para obter mais informações, consulte [Recuperando informações armazenadas em atributos](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="a1890-118">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>  
  
-   <span data-ttu-id="a1890-119">Para examinar e instanciar tipos em um assembly.</span><span class="sxs-lookup"><span data-stu-id="a1890-119">For examining and instantiating types in an assembly.</span></span>  
  
-   <span data-ttu-id="a1890-120">Para criar novos tipos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a1890-120">For building new types at runtime.</span></span> <span data-ttu-id="a1890-121">Usar as classes em <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="a1890-121">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
-   <span data-ttu-id="a1890-122">Para executar a associação tardia, acessar métodos em tipos criados em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a1890-122">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="a1890-123">Consulte o tópico [Carregando e usando tipos dinamicamente](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="a1890-123">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a1890-124">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="a1890-124">Related Sections</span></span>  
 <span data-ttu-id="a1890-125">Para saber mais:</span><span class="sxs-lookup"><span data-stu-id="a1890-125">For more information:</span></span>  
  
-   [<span data-ttu-id="a1890-126">Reflexão</span><span class="sxs-lookup"><span data-stu-id="a1890-126">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
  
-   [<span data-ttu-id="a1890-127">Exibindo informações de tipo</span><span class="sxs-lookup"><span data-stu-id="a1890-127">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
-   [<span data-ttu-id="a1890-128">Reflexão e tipos genéricos</span><span class="sxs-lookup"><span data-stu-id="a1890-128">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
-   <xref:System.Reflection.Emit>  
  
-   [<span data-ttu-id="a1890-129">Recuperando informações armazenadas em atributos</span><span class="sxs-lookup"><span data-stu-id="a1890-129">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a><span data-ttu-id="a1890-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1890-130">See Also</span></span>  
 [<span data-ttu-id="a1890-131">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="a1890-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a1890-132">Assemblies no Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="a1890-132">Assemblies in the Common Language Runtime</span></span>](../../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
