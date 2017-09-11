---
title: "Como implementar e chamar um método de extensão personalizado (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8c1c26640c550ce2b16ffafd59430e92189764f9
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a><span data-ttu-id="9b73b-102">Como implementar e chamar um método de extensão personalizado (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="9b73b-102">How to: Implement and Call a Custom Extension Method (C# Programming Guide)</span></span>
<span data-ttu-id="9b73b-103">Este tópico mostra como implementar seus próprios métodos de extensão para qualquer tipo na [biblioteca de classes .NET Framework](http://go.microsoft.com/fwlink/?LinkID=217856) ou qualquer outro tipo .NET que você desejar estender.</span><span class="sxs-lookup"><span data-stu-id="9b73b-103">This topic shows how to implement your own extension methods for any type in the [.NET Framework Class Library](http://go.microsoft.com/fwlink/?LinkID=217856), or any other .NET type that you want to extend.</span></span> <span data-ttu-id="9b73b-104">O código de cliente pode usar seus métodos de extensão, adicionando uma referência à DLL que os contém e adicionando uma diretiva [using](../../../csharp/language-reference/keywords/using-directive.md) que especifica o namespace no qual os métodos de extensão são definidos.</span><span class="sxs-lookup"><span data-stu-id="9b73b-104">Client code can use your extension methods by adding a reference to the DLL that contains them, and adding a [using](../../../csharp/language-reference/keywords/using-directive.md) directive that specifies the namespace in which the extension methods are defined.</span></span>  
  
## <a name="to-define-and-call-the-extension-method"></a><span data-ttu-id="9b73b-105">Para definir e chamar o método de extensão</span><span class="sxs-lookup"><span data-stu-id="9b73b-105">To define and call the extension method</span></span>  
  
1.  <span data-ttu-id="9b73b-106">Defina uma [classe](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md) estática para conter o método de extensão.</span><span class="sxs-lookup"><span data-stu-id="9b73b-106">Define a static [class](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md) to contain the extension method.</span></span>  
  
     <span data-ttu-id="9b73b-107">A classe deve estar visível para o código de cliente.</span><span class="sxs-lookup"><span data-stu-id="9b73b-107">The class must be visible to client code.</span></span> <span data-ttu-id="9b73b-108">Para obter mais informações sobre regras de acessibilidade, consulte [Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="9b73b-108">For more information about accessibility rules, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
2.  <span data-ttu-id="9b73b-109">Implemente o método de extensão como um método estático com, pelo menos, a mesma visibilidade da classe que a contém.</span><span class="sxs-lookup"><span data-stu-id="9b73b-109">Implement the extension method as a static method with at least the same visibility as the containing class.</span></span>  
  
3.  <span data-ttu-id="9b73b-110">O primeiro parâmetro do método especifica o tipo no qual o método opera. Ele deve ser precedido pelo modificador [this](../../../csharp/language-reference/keywords/this.md).</span><span class="sxs-lookup"><span data-stu-id="9b73b-110">The first parameter of the method specifies the type that the method operates on; it must be preceded with the [this](../../../csharp/language-reference/keywords/this.md) modifier.</span></span>  
  
4.  <span data-ttu-id="9b73b-111">No código de chamada, adicione uma diretiva `using` para especificar o [namespace](../../../csharp/language-reference/keywords/namespace.md) que contém a classe do método de extensão.</span><span class="sxs-lookup"><span data-stu-id="9b73b-111">In the calling code, add a `using` directive to specify the [namespace](../../../csharp/language-reference/keywords/namespace.md) that contains the extension method class.</span></span>  
  
5.  <span data-ttu-id="9b73b-112">Chame os métodos como se fossem métodos de instância no tipo.</span><span class="sxs-lookup"><span data-stu-id="9b73b-112">Call the methods as if they were instance methods on the type.</span></span>  
  
     <span data-ttu-id="9b73b-113">Observe que o primeiro parâmetro não é especificado pelo código de chamada porque ele representa o tipo no qual o operador está sendo aplicado e o compilador já conhece o tipo do objeto.</span><span class="sxs-lookup"><span data-stu-id="9b73b-113">Note that the first parameter is not specified by calling code because it represents the type on which the operator is being applied, and the compiler already knows the type of your object.</span></span> <span data-ttu-id="9b73b-114">Você só precisa fornecer argumentos para os parâmetros de 2 até o `n`.</span><span class="sxs-lookup"><span data-stu-id="9b73b-114">You only have to provide arguments for parameters 2 through `n`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b73b-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9b73b-115">Example</span></span>  
 <span data-ttu-id="9b73b-116">O exemplo a seguir implementa um método de extensão chamado `WordCount` na classe `CustomExtensions.StringExtension`.</span><span class="sxs-lookup"><span data-stu-id="9b73b-116">The following example implements an extension method named `WordCount` in the `CustomExtensions.StringExtension` class.</span></span> <span data-ttu-id="9b73b-117">O método funciona na classe <xref:System.String>, que é especificada como o primeiro parâmetro do método.</span><span class="sxs-lookup"><span data-stu-id="9b73b-117">The method operates on the <xref:System.String> class, which is specified as the first method parameter.</span></span> <span data-ttu-id="9b73b-118">O namespace `CustomExtensions` é importado para o namespace do aplicativo e o método é chamado dentro do método `Main`.</span><span class="sxs-lookup"><span data-stu-id="9b73b-118">The `CustomExtensions` namespace is imported into the application namespace, and the method is called inside the `Main` method.</span></span>  
  
 <span data-ttu-id="9b73b-119">[!code-cs[csProgGuideExtensionMethods#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-and-call-a-custom-extension-method_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="9b73b-119">[!code-cs[csProgGuideExtensionMethods#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-and-call-a-custom-extension-method_1.cs)]</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9b73b-120">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="9b73b-120">Compiling the Code</span></span>  
 <span data-ttu-id="9b73b-121">Para executar esse código, copie e cole-o em um console de projeto de aplicativo do Visual C# que foi criado no [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9b73b-121">To run this code, copy and paste it into a Visual C# console application project that has been created in [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)].</span></span> <span data-ttu-id="9b73b-122">Por padrão, esse projeto é direcionado para a versão 3.5 do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] e ele tem uma referência ao System.Core.dll e uma diretriz `using` para System.Linq.</span><span class="sxs-lookup"><span data-stu-id="9b73b-122">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it has a reference to System.Core.dll and a `using` directive for System.Linq.</span></span> <span data-ttu-id="9b73b-123">Se um ou mais desses requisitos estiverem ausentes no projeto, você poderá adicioná-los manualmente.</span><span class="sxs-lookup"><span data-stu-id="9b73b-123">If one or more of these requirements are missing from the project, you can add them manually.</span></span>   
  
## <a name="net-framework-security"></a><span data-ttu-id="9b73b-124">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9b73b-124">.NET Framework Security</span></span>  
 <span data-ttu-id="9b73b-125">Os métodos de extensão não apresentam nenhuma vulnerabilidade de segurança específica.</span><span class="sxs-lookup"><span data-stu-id="9b73b-125">Extension methods present no specific security vulnerabilities.</span></span> <span data-ttu-id="9b73b-126">Eles nunca podem ser usados para representar os métodos existentes em um tipo, porque todos os conflitos de nome são resolvidos em favor da instância ou do método estático, definidos pelo próprio tipo.</span><span class="sxs-lookup"><span data-stu-id="9b73b-126">They can never be used to impersonate existing methods on a type, because all name collisions are resolved in favor of the instance or static method defined by the type itself.</span></span> <span data-ttu-id="9b73b-127">Os métodos de extensão não podem acessar nenhum dado particular na classe estendida.</span><span class="sxs-lookup"><span data-stu-id="9b73b-127">Extension methods cannot access any private data in the extended class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b73b-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9b73b-128">See Also</span></span>  
 <span data-ttu-id="9b73b-129">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="9b73b-129">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="9b73b-130">[Métodos de Extensão](../../../csharp/programming-guide/classes-and-structs/extension-methods.md) </span><span class="sxs-lookup"><span data-stu-id="9b73b-130">[Extension Methods](../../../csharp/programming-guide/classes-and-structs/extension-methods.md) </span></span>  
 <span data-ttu-id="9b73b-131">[LINQ (Consulta Integrada à Linguagem)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) </span><span class="sxs-lookup"><span data-stu-id="9b73b-131">[LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) </span></span>  
 <span data-ttu-id="9b73b-132">[Classes estáticas e membros de classes estáticas](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md) </span><span class="sxs-lookup"><span data-stu-id="9b73b-132">[Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md) </span></span>  
 <span data-ttu-id="9b73b-133">[protected](../../../csharp/language-reference/keywords/protected.md) </span><span class="sxs-lookup"><span data-stu-id="9b73b-133">[protected](../../../csharp/language-reference/keywords/protected.md) </span></span>  
 <span data-ttu-id="9b73b-134">[internal](../../../csharp/language-reference/keywords/internal.md) </span><span class="sxs-lookup"><span data-stu-id="9b73b-134">[internal](../../../csharp/language-reference/keywords/internal.md) </span></span>  
 <span data-ttu-id="9b73b-135">[public](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="9b73b-135">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="9b73b-136">[this](../../../csharp/language-reference/keywords/this.md) </span><span class="sxs-lookup"><span data-stu-id="9b73b-136">[this](../../../csharp/language-reference/keywords/this.md) </span></span>  
 [<span data-ttu-id="9b73b-137">namespace</span><span class="sxs-lookup"><span data-stu-id="9b73b-137">namespace</span></span>](../../../csharp/language-reference/keywords/namespace.md)

