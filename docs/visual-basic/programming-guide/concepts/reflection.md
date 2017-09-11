---
title: "Reflexão (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: acfcb519128de0d616757398c94ec70dc7de6ef1
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="reflection-visual-basic"></a><span data-ttu-id="6f5c6-102">Reflexão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f5c6-102">Reflection (Visual Basic)</span></span>
<span data-ttu-id="6f5c6-103">Reflexão fornece objetos (do tipo <xref:System.Type>) que descrevem os assemblies, módulos e tipos.</xref:System.Type></span><span class="sxs-lookup"><span data-stu-id="6f5c6-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="6f5c6-104">Você pode usar reflexão dinamicamente criar uma instância de um tipo, o tipo de associação a um objeto existente, ou obter o tipo de um objeto existente e chamar seus métodos ou acessar suas propriedades e campos.</span><span class="sxs-lookup"><span data-stu-id="6f5c6-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="6f5c6-105">Se você estiver usando atributos no seu código, reflexão permite acessá-los.</span><span class="sxs-lookup"><span data-stu-id="6f5c6-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="6f5c6-106">Para obter mais informações, consulte [atributos](https://msdn.microsoft.com/library/5x6cd29c).</span><span class="sxs-lookup"><span data-stu-id="6f5c6-106">For more information, see [Attributes](https://msdn.microsoft.com/library/5x6cd29c).</span></span>  
  
 <span data-ttu-id="6f5c6-107">Aqui está um exemplo simples de reflexão usando o método estático `GetType` - herdadas por todos os tipos do `Object` base class - para obter o tipo de uma variável:</span><span class="sxs-lookup"><span data-stu-id="6f5c6-107">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 <span data-ttu-id="6f5c6-108">A saída é:</span><span class="sxs-lookup"><span data-stu-id="6f5c6-108">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="6f5c6-109">O exemplo a seguir usa a reflexão para obter o nome completo do assembly carregado.</span><span class="sxs-lookup"><span data-stu-id="6f5c6-109">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 <span data-ttu-id="6f5c6-110">A saída é:</span><span class="sxs-lookup"><span data-stu-id="6f5c6-110">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a><span data-ttu-id="6f5c6-111">Visão geral de reflexão</span><span class="sxs-lookup"><span data-stu-id="6f5c6-111">Reflection Overview</span></span>  
 <span data-ttu-id="6f5c6-112">A reflexão é útil nas seguintes situações:</span><span class="sxs-lookup"><span data-stu-id="6f5c6-112">Reflection is useful in the following situations:</span></span>  
  
-   <span data-ttu-id="6f5c6-113">Quando você tem que acessar atributos nos metadados do seu programa.</span><span class="sxs-lookup"><span data-stu-id="6f5c6-113">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="6f5c6-114">Para obter mais informações, consulte [Recuperando informações armazenadas em atributos](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c).</span><span class="sxs-lookup"><span data-stu-id="6f5c6-114">For more information, see [Retrieving Information Stored in Attributes](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c).</span></span>  
  
-   <span data-ttu-id="6f5c6-115">Para examinar e instanciar tipos em um assembly.</span><span class="sxs-lookup"><span data-stu-id="6f5c6-115">For examining and instantiating types in an assembly.</span></span>  
  
-   <span data-ttu-id="6f5c6-116">Para criar novos tipos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6f5c6-116">For building new types at runtime.</span></span> <span data-ttu-id="6f5c6-117">Usar as classes em <xref:System.Reflection.Emit>.</xref:System.Reflection.Emit></span><span class="sxs-lookup"><span data-stu-id="6f5c6-117">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
-   <span data-ttu-id="6f5c6-118">Para executar ligação tardia, acessar métodos em tipos criados em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6f5c6-118">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="6f5c6-119">Consulte o tópico [Carregando dinamicamente e usando tipos](http://msdn.microsoft.com/library/db985bec-5942-40ec-b13a-771ae98623dc).</span><span class="sxs-lookup"><span data-stu-id="6f5c6-119">See the topic [Dynamically Loading and Using Types](http://msdn.microsoft.com/library/db985bec-5942-40ec-b13a-771ae98623dc).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6f5c6-120">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="6f5c6-120">Related Sections</span></span>  
 <span data-ttu-id="6f5c6-121">Para saber mais:</span><span class="sxs-lookup"><span data-stu-id="6f5c6-121">For more information:</span></span>  
  
-   [<span data-ttu-id="6f5c6-122">Reflexão</span><span class="sxs-lookup"><span data-stu-id="6f5c6-122">Reflection</span></span>](http://msdn.microsoft.com/library/d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775)  
  
-   [<span data-ttu-id="6f5c6-123">Exibindo informações de tipo</span><span class="sxs-lookup"><span data-stu-id="6f5c6-123">Viewing Type Information</span></span>](http://msdn.microsoft.com/library/7e7303a9-4064-4738-b4e7-b75974ed70d2)  
  
-   [<span data-ttu-id="6f5c6-124">Reflexão e tipos genéricos</span><span class="sxs-lookup"><span data-stu-id="6f5c6-124">Reflection and Generic Types</span></span>](http://msdn.microsoft.com/library/f7180fc5-dd41-42d4-8a8e-1b34288e06de)  
  
-   <span data-ttu-id="6f5c6-125"><xref:System.Reflection.Emit></xref:System.Reflection.Emit></span><span class="sxs-lookup"><span data-stu-id="6f5c6-125"><xref:System.Reflection.Emit></span></span>  
  
-   [<span data-ttu-id="6f5c6-126">Recuperando informações armazenadas em atributos</span><span class="sxs-lookup"><span data-stu-id="6f5c6-126">Retrieving Information Stored in Attributes</span></span>](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c)  
  
## <a name="see-also"></a><span data-ttu-id="6f5c6-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f5c6-127">See Also</span></span>  
 <span data-ttu-id="6f5c6-128">[Guia de programação em Visual Basic](../../../visual-basic/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="6f5c6-128">[Visual Basic Programming Guide](../../../visual-basic/programming-guide/index.md) </span></span>  
<span data-ttu-id="6f5c6-129"> [Assemblies no Common Language Runtime](https://msdn.microsoft.com/library/k3677y81)</span><span class="sxs-lookup"><span data-stu-id="6f5c6-129"> [Assemblies in the Common Language Runtime](https://msdn.microsoft.com/library/k3677y81)</span></span>
