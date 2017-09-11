---
title: "&quot;&lt;expressão&gt;&quot; não pode ser usado como restrição de tipo | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32061
- vbc32061
dev_langs:
- VB
helpviewer_keywords:
- BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
caps.latest.revision: 18
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
ms.openlocfilehash: 53e540c0009969009b8fecfabb4091999c119cb3
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="39ltexpressiongt39-cannot-be-used-as-a-type-constraint"></a><span data-ttu-id="2a069-102">'&lt;expressão&gt;' não pode ser usado como restrição de tipo</span><span class="sxs-lookup"><span data-stu-id="2a069-102">&#39;&lt;expression&gt;&#39; cannot be used as a type constraint</span></span>
<span data-ttu-id="2a069-103">Uma lista de restrições inclui uma expressão que não representa uma restrição válida em um parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="2a069-103">A constraint list includes an expression that does not represent a valid constraint on a type parameter.</span></span>  
  
 <span data-ttu-id="2a069-104">Uma lista de restrições impõe exigências no tipo de argumento passado para o parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="2a069-104">A constraint list imposes requirements on the type argument passed to the type parameter.</span></span> <span data-ttu-id="2a069-105">Você pode especificar os seguintes requisitos em qualquer combinação:</span><span class="sxs-lookup"><span data-stu-id="2a069-105">You can specify the following requirements in any combination:</span></span>  
  
-   <span data-ttu-id="2a069-106">O argumento de tipo deve implementar uma ou mais interfaces</span><span class="sxs-lookup"><span data-stu-id="2a069-106">The type argument must implement one or more interfaces</span></span>  
  
-   <span data-ttu-id="2a069-107">O argumento de tipo deve herdar de no máximo uma classe</span><span class="sxs-lookup"><span data-stu-id="2a069-107">The type argument must inherit from at most one class</span></span>  
  
-   <span data-ttu-id="2a069-108">O argumento de tipo deve expor um construtor sem parâmetros que pode acessar o código de criação (incluem o `New` restrição)</span><span class="sxs-lookup"><span data-stu-id="2a069-108">The type argument must expose a parameterless constructor that the creating code can access (include the `New` constraint)</span></span>  
  
 <span data-ttu-id="2a069-109">Se você não incluir qualquer interface ou classe específica na lista de restrição, você pode impor uma necessidade geral, especificando um destes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="2a069-109">If you do not include any specific class or interface in the constraint list, you can impose a more general requirement by specifying one of the following:</span></span>  
  
-   <span data-ttu-id="2a069-110">O argumento de tipo deve ser um tipo de valor (inclua a `Structure` restrição)</span><span class="sxs-lookup"><span data-stu-id="2a069-110">The type argument must be a value type (include the `Structure` constraint)</span></span>  
  
-   <span data-ttu-id="2a069-111">O argumento de tipo deve ser um tipo de referência (incluem o `Class` restrição)</span><span class="sxs-lookup"><span data-stu-id="2a069-111">The type argument must be a reference type (include the `Class` constraint)</span></span>  
  
 <span data-ttu-id="2a069-112">Não é possível especificar `Structure` e `Class` para o mesmo tipo de parâmetro e você não pode especificar uma mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="2a069-112">You cannot specify both `Structure` and `Class` for the same type parameter, and you cannot specify either one more than once.</span></span>  
  
 <span data-ttu-id="2a069-113">**ID do erro:** BC32061</span><span class="sxs-lookup"><span data-stu-id="2a069-113">**Error ID:** BC32061</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2a069-114">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="2a069-114">To correct this error</span></span>  
  
-   <span data-ttu-id="2a069-115">Verifique se a expressão e seus elementos estão escritos corretamente.</span><span class="sxs-lookup"><span data-stu-id="2a069-115">Verify that the expression and its elements are spelled correctly.</span></span>  
  
-   <span data-ttu-id="2a069-116">Se a expressão não está qualificada para a lista anterior de requisitos, remova-o da lista de restrições.</span><span class="sxs-lookup"><span data-stu-id="2a069-116">If the expression does not qualify for the preceding list of requirements, remove it from the constraint list.</span></span>  
  
-   <span data-ttu-id="2a069-117">Se a expressão fizer referência a uma interface ou classe, verifique se o compilador tem acesso a essa interface ou classe.</span><span class="sxs-lookup"><span data-stu-id="2a069-117">If the expression refers to an interface or class, verify that the compiler has access to that interface or class.</span></span> <span data-ttu-id="2a069-118">Talvez você precise qualificar seu nome, e talvez seja necessário adicionar uma referência ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="2a069-118">You might need to qualify its name, and you might need to add a reference to your project.</span></span> <span data-ttu-id="2a069-119">Para obter mais informações, consulte "Referências a projetos" [referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="2a069-119">For more information, see "References to Projects" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a069-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a069-120">See Also</span></span>  
 <span data-ttu-id="2a069-121">[Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span><span class="sxs-lookup"><span data-stu-id="2a069-121">[Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span></span>  
<span data-ttu-id="2a069-122"> [Tipos de valor e tipos de referência](../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="2a069-122"> [Value Types and Reference Types](../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span></span>  
<span data-ttu-id="2a069-123"> [Referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md) </span><span class="sxs-lookup"><span data-stu-id="2a069-123"> [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md) </span></span>  
<span data-ttu-id="2a069-124"> [NIB: como adicionar ou remover referências usando a caixa de diálogo Adicionar Referência](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)</span><span class="sxs-lookup"><span data-stu-id="2a069-124"> [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)</span></span>
