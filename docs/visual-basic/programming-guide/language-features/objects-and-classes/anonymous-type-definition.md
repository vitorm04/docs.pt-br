---
title: "Definição de tipo anônimo (Visual Basic) | Documentos do Microsoft"
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
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
caps.latest.revision: 21
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
ms.openlocfilehash: 8e9407cf25bbc88fc71419b6013d33684d73c4fc
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="anonymous-type-definition-visual-basic"></a><span data-ttu-id="2591c-102">Definição do tipo anônimo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2591c-102">Anonymous Type Definition (Visual Basic)</span></span>
<span data-ttu-id="2591c-103">Em resposta à declaração de uma instância de um tipo anônimo, o compilador cria uma nova definição de classe que contém as propriedades especificadas para o tipo.</span><span class="sxs-lookup"><span data-stu-id="2591c-103">In response to the declaration of an instance of an anonymous type, the compiler creates a new class definition that contains the specified properties for the type.</span></span>  
  
## <a name="compiler-generated-code"></a><span data-ttu-id="2591c-104">Código gerado pelo compilador</span><span class="sxs-lookup"><span data-stu-id="2591c-104">Compiler-Generated Code</span></span>  
 <span data-ttu-id="2591c-105">Para a seguinte definição de `product`, o compilador cria uma nova definição de classe que contém propriedades `Name`, `Price`, e `OnHand`.</span><span class="sxs-lookup"><span data-stu-id="2591c-105">For the following definition of `product`, the compiler creates a new class definition that contains properties `Name`, `Price`, and `OnHand`.</span></span>  
  
 <span data-ttu-id="2591c-106">[!code-vb[25 VbVbalrAnonymousTypes](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="2591c-106">[!code-vb[VbVbalrAnonymousTypes#25](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_1.vb)]</span></span>  
  
 <span data-ttu-id="2591c-107">A definição de classe contém definições de propriedade semelhantes ao seguinte.</span><span class="sxs-lookup"><span data-stu-id="2591c-107">The class definition contains property definitions similar to the following.</span></span> <span data-ttu-id="2591c-108">Observe que não há nenhum `Set` método para as propriedades de chave.</span><span class="sxs-lookup"><span data-stu-id="2591c-108">Notice that there is no `Set` method for the key properties.</span></span> <span data-ttu-id="2591c-109">Os valores das propriedades de chave são somente leitura.</span><span class="sxs-lookup"><span data-stu-id="2591c-109">The values of key properties are read-only.</span></span>  
  
```vb  
Public Class $Anonymous1  
    Private _name As String  
    Private _price As Double  
    Private _onHand As Integer  
     Public ReadOnly Property Name() As String  
        Get  
            Return _name  
        End Get  
    End Property  
  
    Public ReadOnly Property Price() As Double  
        Get  
            Return _price  
        End Get  
    End Property  
  
    Public Property OnHand() As Integer  
        Get  
            Return _onHand  
        End Get  
        Set(ByVal Value As Integer)  
            _onHand = Value  
        End Set  
    End Property  
  
End Class  
```  
  
 <span data-ttu-id="2591c-110">Além disso, definições de tipo anônimo contêm um construtor padrão.</span><span class="sxs-lookup"><span data-stu-id="2591c-110">In addition, anonymous type definitions contain a default constructor.</span></span> <span data-ttu-id="2591c-111">Os construtores que exigem parâmetros não são permitidos.</span><span class="sxs-lookup"><span data-stu-id="2591c-111">Constructors that require parameters are not permitted.</span></span>  
  
 <span data-ttu-id="2591c-112">Se uma declaração de tipo anônimo contém pelo menos uma propriedade de chave, a definição de tipo substitui três membros herdados <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>e <xref:System.Object.ToString%2A>.</xref:System.Object.ToString%2A> </xref:System.Object.GetHashCode%2A> </xref:System.Object.Equals%2A> </xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="2591c-112">If an anonymous type declaration contains at least one key property, the type definition overrides three members inherited from <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="2591c-113">Se nenhuma propriedade de chave é declarada, somente <xref:System.Object.ToString%2A>é substituído.</xref:System.Object.ToString%2A></span><span class="sxs-lookup"><span data-stu-id="2591c-113">If no key properties are declared, only <xref:System.Object.ToString%2A> is overridden.</span></span> <span data-ttu-id="2591c-114">As substituições fornecem a seguinte funcionalidade:</span><span class="sxs-lookup"><span data-stu-id="2591c-114">The overrides provide the following functionality:</span></span>  
  
-   <span data-ttu-id="2591c-115">`Equals`Retorna `True` se duas instâncias de tipo anônimo se a mesma instância, ou se eles atendem às seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="2591c-115">`Equals` returns `True` if two anonymous type instances are the same instance, or if they meet the following conditions:</span></span>  
  
    -   <span data-ttu-id="2591c-116">Eles têm o mesmo número de propriedades.</span><span class="sxs-lookup"><span data-stu-id="2591c-116">They have the same number of properties.</span></span>  
  
    -   <span data-ttu-id="2591c-117">As propriedades são declaradas na mesma ordem, com os mesmos nomes e os mesmos inferidos tipos.</span><span class="sxs-lookup"><span data-stu-id="2591c-117">The properties are declared in the same order, with the same names and the same inferred types.</span></span> <span data-ttu-id="2591c-118">Nome comparações não diferenciam maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="2591c-118">Name comparisons are not case-sensitive.</span></span>  
  
    -   <span data-ttu-id="2591c-119">Pelo menos uma das propriedades é uma propriedade de chave e o `Key` palavra-chave é aplicada às mesmas propriedades.</span><span class="sxs-lookup"><span data-stu-id="2591c-119">At least one of the properties is a key property, and the `Key` keyword is applied to the same properties.</span></span>  
  
    -   <span data-ttu-id="2591c-120">Comparação entre cada par correspondente de propriedades chave retorna `True`.</span><span class="sxs-lookup"><span data-stu-id="2591c-120">Comparison of each corresponding pair of key properties returns `True`.</span></span>  
  
     <span data-ttu-id="2591c-121">Por exemplo, nos exemplos a seguir, `Equals` retorna `True` apenas para `employee01` e `employee08`.</span><span class="sxs-lookup"><span data-stu-id="2591c-121">For example, in the following examples, `Equals` returns `True` only for `employee01` and `employee08`.</span></span> <span data-ttu-id="2591c-122">O comentário antes de cada linha especifica o motivo por que não coincide com a nova instância `employee01`.</span><span class="sxs-lookup"><span data-stu-id="2591c-122">The comment before each line specifies the reason why the new instance does not match `employee01`.</span></span>  
  
     <span data-ttu-id="2591c-123">[!code-vb[VbVbalrAnonymousTypes&#24;](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="2591c-123">[!code-vb[VbVbalrAnonymousTypes#24](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_2.vb)]</span></span>  
  
-   <span data-ttu-id="2591c-124">`GetHashcode`Fornece um algoritmo GetHashCode adequadamente exclusivo.</span><span class="sxs-lookup"><span data-stu-id="2591c-124">`GetHashcode` provides an appropriately unique GetHashCode algorithm.</span></span> <span data-ttu-id="2591c-125">O algoritmo usa somente as propriedades da chave para calcular o código hash.</span><span class="sxs-lookup"><span data-stu-id="2591c-125">The algorithm uses only the key properties to compute the hash code.</span></span>  
  
-   <span data-ttu-id="2591c-126">`ToString`Retorna uma cadeia de caracteres de valores de propriedade concatenados, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="2591c-126">`ToString` returns a string of concatenated property values, as shown in the following example.</span></span> <span data-ttu-id="2591c-127">Chave e propriedades de chave não são incluídas.</span><span class="sxs-lookup"><span data-stu-id="2591c-127">Both key and non-key properties are included.</span></span>  
  
     <span data-ttu-id="2591c-128">[!code-vb[29 VbVbalrAnonymousTypes](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="2591c-128">[!code-vb[VbVbalrAnonymousTypes#29](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-type-definition_3.vb)]</span></span>  
  
 <span data-ttu-id="2591c-129">Propriedades explicitamente nomeadas de um tipo anônimo não entram em conflito com esses métodos gerados.</span><span class="sxs-lookup"><span data-stu-id="2591c-129">Explicitly named properties of an anonymous type cannot conflict with these generated methods.</span></span> <span data-ttu-id="2591c-130">Ou seja, você não pode usar `.Equals`, `.GetHashCode`, ou `.ToString` para nomear uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="2591c-130">That is, you cannot use `.Equals`, `.GetHashCode`, or `.ToString` to name a property.</span></span>  
  
 <span data-ttu-id="2591c-131">Tipo anônimo definições que incluem pelo menos uma propriedade de chave também implementa o <xref:System.IEquatable%601?displayProperty=fullName>interface, onde `T` é o tipo do tipo anônimo.</xref:System.IEquatable%601?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="2591c-131">Anonymous type definitions that include at least one key property also implement the <xref:System.IEquatable%601?displayProperty=fullName> interface, where `T` is the type of the anonymous type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2591c-132">Tipo anônimo declarações criar o mesmo tipo anônimo somente se ocorrerem no mesmo assembly, suas propriedades possuem os mesmos nomes e os mesmos inferidos tipos, as propriedades são declaradas na mesma ordem e as mesmas propriedades são marcadas como propriedades de chave.</span><span class="sxs-lookup"><span data-stu-id="2591c-132">Anonymous type declarations create the same anonymous type only if they occur in the same assembly, their properties have the same names and the same inferred types, the properties are declared in the same order, and the same properties are marked as key properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2591c-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2591c-133">See Also</span></span>  
 <span data-ttu-id="2591c-134">[Tipos anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="2591c-134">[Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span></span>  
<span data-ttu-id="2591c-135"> [Como inferir nomes e tipos de propriedade na declaração de tipo anônimo](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)</span><span class="sxs-lookup"><span data-stu-id="2591c-135"> [How to: Infer Property Names and Types in Anonymous Type Declarations](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)</span></span>
