---
title: Tipo de dados do objeto | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Object
- vb.Variant
dev_langs:
- VB
helpviewer_keywords:
- object variables, Object type
- data types [Visual Basic], assigning
- Object data type
- Object data type, reference
ms.assetid: 61ea4a7c-3b3d-48d4-adc4-eacfa91779b2
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: f4894565a020dfe00218ad5535698d0ec89be3aa
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="object-data-type"></a><span data-ttu-id="9935c-102">Tipo de dados Object</span><span class="sxs-lookup"><span data-stu-id="9935c-102">Object Data Type</span></span>
<span data-ttu-id="9935c-103">Contém os endereços que se referem a objetos.</span><span class="sxs-lookup"><span data-stu-id="9935c-103">Holds addresses that refer to objects.</span></span> <span data-ttu-id="9935c-104">Você pode atribuir qualquer tipo de referência (string, array, classe ou interface) para um `Object` variável.</span><span class="sxs-lookup"><span data-stu-id="9935c-104">You can assign any reference type (string, array, class, or interface) to an `Object` variable.</span></span> <span data-ttu-id="9935c-105">Um `Object` variável também pode se referir aos dados de qualquer tipo de valor (numérico, `Boolean`, `Char`, `Date`, estrutura, ou enumeração).</span><span class="sxs-lookup"><span data-stu-id="9935c-105">An `Object` variable can also refer to data of any value type (numeric, `Boolean`, `Char`, `Date`, structure, or enumeration).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9935c-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="9935c-106">Remarks</span></span>  
 <span data-ttu-id="9935c-107">O `Object` tipo de dados pode apontar para dados de qualquer tipo de dados, incluindo qualquer instância do objeto aplicativo reconhece.</span><span class="sxs-lookup"><span data-stu-id="9935c-107">The `Object` data type can point to data of any data type, including any object instance your application recognizes.</span></span> <span data-ttu-id="9935c-108">Use `Object` quando você não souber em tempo de compilação qual tipo de dados a variável pode apontar.</span><span class="sxs-lookup"><span data-stu-id="9935c-108">Use `Object` when you do not know at compile time what data type the variable might point to.</span></span>  
  
 <span data-ttu-id="9935c-109">O valor padrão de `Object` é `Nothing` (uma referência nula).</span><span class="sxs-lookup"><span data-stu-id="9935c-109">The default value of `Object` is `Nothing` (a null reference).</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="9935c-110">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="9935c-110">Data Types</span></span>  
 <span data-ttu-id="9935c-111">Você pode atribuir uma variável, uma constante ou uma expressão de qualquer tipo de dados para um `Object` variável.</span><span class="sxs-lookup"><span data-stu-id="9935c-111">You can assign a variable, constant, or expression of any data type to an `Object` variable.</span></span> <span data-ttu-id="9935c-112">Para determinar o tipo de dados um `Object` variável atualmente se refere, você pode usar o <xref:System.Type.GetTypeCode%2A>método de <xref:System.Type?displayProperty=fullName>classe.</xref:System.Type?displayProperty=fullName> </xref:System.Type.GetTypeCode%2A></span><span class="sxs-lookup"><span data-stu-id="9935c-112">To determine the data type an `Object` variable currently refers to, you can use the <xref:System.Type.GetTypeCode%2A> method of the <xref:System.Type?displayProperty=fullName> class.</span></span> <span data-ttu-id="9935c-113">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="9935c-113">The following example illustrates this.</span></span>  
  
```  
Dim myObject As Object  
' Suppose myObject has now had something assigned to it.  
Dim datTyp As Integer  
datTyp = Type.GetTypeCode(myObject.GetType())  
```  
  
 <span data-ttu-id="9935c-114">O `Object` é um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="9935c-114">The `Object` data type is a reference type.</span></span> <span data-ttu-id="9935c-115">No entanto, o Visual Basic trata uma `Object` variável como um tipo de valor quando ela se refere aos dados de um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="9935c-115">However, Visual Basic treats an `Object` variable as a value type when it refers to data of a value type.</span></span>  
  
## <a name="storage"></a><span data-ttu-id="9935c-116">Armazenamento</span><span class="sxs-lookup"><span data-stu-id="9935c-116">Storage</span></span>  
 <span data-ttu-id="9935c-117">Qualquer tipo de dados que ela se refere, uma `Object` variável não contém o valor dos dados em si, mas em vez disso, um ponteiro para o valor.</span><span class="sxs-lookup"><span data-stu-id="9935c-117">Whatever data type it refers to, an `Object` variable does not contain the data value itself, but rather a pointer to the value.</span></span> <span data-ttu-id="9935c-118">Ela sempre usa quatro bytes na memória do computador, mas isso não inclui o armazenamento de dados que representa o valor da variável.</span><span class="sxs-lookup"><span data-stu-id="9935c-118">It always uses four bytes in computer memory, but this does not include the storage for the data representing the value of the variable.</span></span> <span data-ttu-id="9935c-119">Por causa do código que usa o ponteiro para localizar os dados, `Object` variáveis contém tipos de valor são um pouco mais lentas para acesso do que explicitamente variáveis digitadas.</span><span class="sxs-lookup"><span data-stu-id="9935c-119">Because of the code that uses the pointer to locate the data, `Object` variables holding value types are slightly slower to access than explicitly typed variables.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="9935c-120">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="9935c-120">Programming Tips</span></span>  
  
-   <span data-ttu-id="9935c-121">**Considerações de interoperabilidade.**</span><span class="sxs-lookup"><span data-stu-id="9935c-121">**Interop Considerations.**</span></span> <span data-ttu-id="9935c-122">Se você estiver fazendo interface com componentes não escritos para o .NET Framework, como objetos de automação ou COM, tenha em mente que tipos de ponteiro em outros ambientes não são compatíveis com o Visual Basic `Object` tipo.</span><span class="sxs-lookup"><span data-stu-id="9935c-122">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that pointer types in other environments are not compatible with the Visual Basic `Object` type.</span></span>  
  
-   <span data-ttu-id="9935c-123">**Desempenho.**</span><span class="sxs-lookup"><span data-stu-id="9935c-123">**Performance.**</span></span> <span data-ttu-id="9935c-124">Uma variável declarada com o `Object` tipo é flexível o suficiente para conter uma referência a qualquer objeto.</span><span class="sxs-lookup"><span data-stu-id="9935c-124">A variable you declare with the `Object` type is flexible enough to contain a reference to any object.</span></span> <span data-ttu-id="9935c-125">No entanto, quando você invoca um método ou propriedade nesse tipo de variável, você sempre provoca *ligação tardia* (em tempo de execução).</span><span class="sxs-lookup"><span data-stu-id="9935c-125">However, when you invoke a method or property on such a variable, you always incur *late binding* (at run time).</span></span> <span data-ttu-id="9935c-126">Para forçar o *vinculação inicial* (em tempo de compilação) e um melhor desempenho, declarar a variável com um nome de classe específico ou convertê-lo para o tipo de dados específico.</span><span class="sxs-lookup"><span data-stu-id="9935c-126">To force *early binding* (at compile time) and better performance, declare the variable with a specific class name, or cast it to the specific data type.</span></span>  
  
     <span data-ttu-id="9935c-127">Quando você declarar uma variável de objeto, tente usar um tipo de classe específico, por exemplo <xref:System.OperatingSystem>, em vez de generalizada `Object` tipo.</xref:System.OperatingSystem></span><span class="sxs-lookup"><span data-stu-id="9935c-127">When you declare an object variable, try to use a specific class type, for example <xref:System.OperatingSystem>, instead of the generalized `Object` type.</span></span> <span data-ttu-id="9935c-128">Você também deve usar a classe mais específica disponível, tais como <xref:System.Windows.Forms.TextBox>em vez de <xref:System.Windows.Forms.Control>, de modo que você pode acessar suas propriedades e métodos.</xref:System.Windows.Forms.Control> </xref:System.Windows.Forms.TextBox></span><span class="sxs-lookup"><span data-stu-id="9935c-128">You should also use the most specific class available, such as <xref:System.Windows.Forms.TextBox> instead of <xref:System.Windows.Forms.Control>, so that you can access its properties and methods.</span></span> <span data-ttu-id="9935c-129">Você pode usar o **Classes** lista no **Pesquisador de objetos** para localizar nomes de classe disponíveis.</span><span class="sxs-lookup"><span data-stu-id="9935c-129">You can usually use the **Classes** list in the **Object Browser** to find available class names.</span></span>  
  
-   <span data-ttu-id="9935c-130">**Ampliação.**</span><span class="sxs-lookup"><span data-stu-id="9935c-130">**Widening.**</span></span> <span data-ttu-id="9935c-131">Todos os tipos de dados e todos os tipos de referência ampliam-se para o `Object` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="9935c-131">All data types and all reference types widen to the `Object` data type.</span></span> <span data-ttu-id="9935c-132">Isso significa que você pode converter qualquer tipo de `Object` sem encontrar uma <xref:System.OverflowException?displayProperty=fullName>erro.</xref:System.OverflowException?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="9935c-132">This means you can convert any type to `Object` without encountering a <xref:System.OverflowException?displayProperty=fullName> error.</span></span>  
  
     <span data-ttu-id="9935c-133">No entanto, se você converter entre tipos de valor e `Object`, Visual Basic executa operações chamadas *conversão boxing* e *unboxing*, que tornam a execução mais lenta.</span><span class="sxs-lookup"><span data-stu-id="9935c-133">However, if you convert between value types and `Object`, Visual Basic performs operations called *boxing* and *unboxing*, which make execution slower.</span></span>  
  
-   <span data-ttu-id="9935c-134">**Caracteres de tipo.**</span><span class="sxs-lookup"><span data-stu-id="9935c-134">**Type Characters.**</span></span> <span data-ttu-id="9935c-135">`Object`não possui caractere de tipo literal ou caractere de tipo identificador.</span><span class="sxs-lookup"><span data-stu-id="9935c-135">`Object` has no literal type character or identifier type character.</span></span>  
  
-   <span data-ttu-id="9935c-136">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="9935c-136">**Framework Type.**</span></span> <span data-ttu-id="9935c-137">O tipo correspondente no .NET Framework é a <xref:System.Object?displayProperty=fullName>classe.</xref:System.Object?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="9935c-137">The corresponding type in the .NET Framework is the <xref:System.Object?displayProperty=fullName> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9935c-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9935c-138">Example</span></span>  
 <span data-ttu-id="9935c-139">O exemplo a seguir ilustra um `Object` variável que aponta para uma instância do objeto.</span><span class="sxs-lookup"><span data-stu-id="9935c-139">The following example illustrates an `Object` variable pointing to an object instance.</span></span>  
  
```  
Dim objDb As Object  
Dim myCollection As New Collection()  
' Suppose myCollection has now been populated.  
objDb = myCollection.Item(1)  
```  
  
## <a name="see-also"></a><span data-ttu-id="9935c-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9935c-140">See Also</span></span>  
 <span data-ttu-id="9935c-141"><xref:System.Object></xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="9935c-141"><xref:System.Object></span></span>   
<span data-ttu-id="9935c-142"> [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="9935c-142"> [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="9935c-143"> [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="9935c-143"> [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span></span>  
<span data-ttu-id="9935c-144"> [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span><span class="sxs-lookup"><span data-stu-id="9935c-144"> [Conversion Summary](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span></span>  
<span data-ttu-id="9935c-145"> [Uso eficiente de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="9935c-145"> [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md) </span></span>  
<span data-ttu-id="9935c-146"> [Como: determinar se dois objetos estão relacionados](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md) </span><span class="sxs-lookup"><span data-stu-id="9935c-146"> [How to: Determine Whether Two Objects Are Related](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md) </span></span>  
<span data-ttu-id="9935c-147"> [Como determinar se dois objetos são idênticos](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)</span><span class="sxs-lookup"><span data-stu-id="9935c-147"> [How to: Determine Whether Two Objects Are Identical](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)</span></span>
