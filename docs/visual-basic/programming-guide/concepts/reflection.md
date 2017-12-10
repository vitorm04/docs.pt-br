---
title: "Reflexão (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8c2ae87eae971129059a7e84b36971c13a5fe71b
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2017
---
# <a name="reflection-visual-basic"></a><span data-ttu-id="5fdf5-102">Reflexão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5fdf5-102">Reflection (Visual Basic)</span></span>
<span data-ttu-id="5fdf5-103">A reflexão fornece objetos (do tipo <xref:System.Type>) que descrevem assemblies, módulos e tipos.</span><span class="sxs-lookup"><span data-stu-id="5fdf5-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="5fdf5-104">É possível usar a reflexão para criar dinamicamente uma instância de um tipo, associar o tipo a um objeto existente ou obter o tipo de um objeto existente e invocar seus métodos ou acessar suas propriedades e campos.</span><span class="sxs-lookup"><span data-stu-id="5fdf5-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="5fdf5-105">Se você estiver usando atributos em seu código, a reflexão permite acessá-los.</span><span class="sxs-lookup"><span data-stu-id="5fdf5-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="5fdf5-106">Para obter mais informações, consulte [Atributos](../../../../docs/standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="5fdf5-106">For more information, see [Attributes](../../../../docs/standard/attributes/index.md).</span></span>  
  
 <span data-ttu-id="5fdf5-107">Veja um exemplo simples de reflexão usando o método estático `GetType` – herdado por todos os tipos da classe base `Object` – para obter o tipo de uma variável:</span><span class="sxs-lookup"><span data-stu-id="5fdf5-107">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 <span data-ttu-id="5fdf5-108">A saída é:</span><span class="sxs-lookup"><span data-stu-id="5fdf5-108">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="5fdf5-109">O exemplo a seguir usa a reflexão para obter o nome completo do assembly carregado.</span><span class="sxs-lookup"><span data-stu-id="5fdf5-109">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 <span data-ttu-id="5fdf5-110">A saída é:</span><span class="sxs-lookup"><span data-stu-id="5fdf5-110">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a><span data-ttu-id="5fdf5-111">Visão geral da reflexão</span><span class="sxs-lookup"><span data-stu-id="5fdf5-111">Reflection Overview</span></span>  
 <span data-ttu-id="5fdf5-112">A reflexão é útil nas seguintes situações:</span><span class="sxs-lookup"><span data-stu-id="5fdf5-112">Reflection is useful in the following situations:</span></span>  
  
-   <span data-ttu-id="5fdf5-113">Quando você precisa acessar atributos nos metadados do seu programa.</span><span class="sxs-lookup"><span data-stu-id="5fdf5-113">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="5fdf5-114">Para obter mais informações, consulte [Recuperando informações armazenadas em atributos](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="5fdf5-114">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>  
  
-   <span data-ttu-id="5fdf5-115">Para examinar e instanciar tipos em um assembly.</span><span class="sxs-lookup"><span data-stu-id="5fdf5-115">For examining and instantiating types in an assembly.</span></span>  
  
-   <span data-ttu-id="5fdf5-116">Para criar novos tipos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5fdf5-116">For building new types at runtime.</span></span> <span data-ttu-id="5fdf5-117">Usar as classes em <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="5fdf5-117">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
-   <span data-ttu-id="5fdf5-118">Para executar a associação tardia, acessar métodos em tipos criados em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5fdf5-118">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="5fdf5-119">Consulte o tópico [Carregando e usando tipos dinamicamente](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="5fdf5-119">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5fdf5-120">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="5fdf5-120">Related Sections</span></span>  
 <span data-ttu-id="5fdf5-121">Para saber mais:</span><span class="sxs-lookup"><span data-stu-id="5fdf5-121">For more information:</span></span>  
  
-   [<span data-ttu-id="5fdf5-122">Reflexão</span><span class="sxs-lookup"><span data-stu-id="5fdf5-122">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
  
-   [<span data-ttu-id="5fdf5-123">Exibindo informações de tipo</span><span class="sxs-lookup"><span data-stu-id="5fdf5-123">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
-   [<span data-ttu-id="5fdf5-124">Reflexão e tipos genéricos</span><span class="sxs-lookup"><span data-stu-id="5fdf5-124">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
-   <xref:System.Reflection.Emit>  
  
-   [<span data-ttu-id="5fdf5-125">Recuperando informações armazenadas em atributos</span><span class="sxs-lookup"><span data-stu-id="5fdf5-125">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a><span data-ttu-id="5fdf5-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5fdf5-126">See Also</span></span>  
 [<span data-ttu-id="5fdf5-127">Guia de programação do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5fdf5-127">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)  
 [<span data-ttu-id="5fdf5-128">Assemblies no Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="5fdf5-128">Assemblies in the Common Language Runtime</span></span>](../../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
