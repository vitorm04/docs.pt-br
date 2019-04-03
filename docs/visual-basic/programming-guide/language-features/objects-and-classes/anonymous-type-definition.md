---
title: Definição do tipo anônimo (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
ms.openlocfilehash: 832d56f5c51aea87185f36ec306c3fec036a40e0
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825541"
---
# <a name="anonymous-type-definition-visual-basic"></a><span data-ttu-id="8c6bb-102">Definição do tipo anônimo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c6bb-102">Anonymous Type Definition (Visual Basic)</span></span>
<span data-ttu-id="8c6bb-103">Em resposta à declaração de uma instância de um tipo anônimo, o compilador cria uma nova definição de classe que contém as propriedades especificadas para o tipo.</span><span class="sxs-lookup"><span data-stu-id="8c6bb-103">In response to the declaration of an instance of an anonymous type, the compiler creates a new class definition that contains the specified properties for the type.</span></span>  
  
## <a name="compiler-generated-code"></a><span data-ttu-id="8c6bb-104">Código gerado pelo compilador</span><span class="sxs-lookup"><span data-stu-id="8c6bb-104">Compiler-Generated Code</span></span>  
 <span data-ttu-id="8c6bb-105">Para a seguinte definição de `product`, o compilador cria uma nova definição de classe que contém as propriedades `Name`, `Price`, e `OnHand`.</span><span class="sxs-lookup"><span data-stu-id="8c6bb-105">For the following definition of `product`, the compiler creates a new class definition that contains properties `Name`, `Price`, and `OnHand`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#25)]  
  
 <span data-ttu-id="8c6bb-106">A definição de classe contém definições de propriedade semelhantes ao seguinte.</span><span class="sxs-lookup"><span data-stu-id="8c6bb-106">The class definition contains property definitions similar to the following.</span></span> <span data-ttu-id="8c6bb-107">Observe que não há nenhum `Set` método para as propriedades de chave.</span><span class="sxs-lookup"><span data-stu-id="8c6bb-107">Notice that there is no `Set` method for the key properties.</span></span> <span data-ttu-id="8c6bb-108">Os valores das propriedades de chave são somente leitura.</span><span class="sxs-lookup"><span data-stu-id="8c6bb-108">The values of key properties are read-only.</span></span>  
  
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
  
 <span data-ttu-id="8c6bb-109">Além disso, as definições de tipo anônimo contém um construtor padrão.</span><span class="sxs-lookup"><span data-stu-id="8c6bb-109">In addition, anonymous type definitions contain a default constructor.</span></span> <span data-ttu-id="8c6bb-110">Os construtores que exigem parâmetros não são permitidos.</span><span class="sxs-lookup"><span data-stu-id="8c6bb-110">Constructors that require parameters are not permitted.</span></span>  
  
 <span data-ttu-id="8c6bb-111">Se uma declaração de tipo anônimo contém pelo menos uma propriedade de chave, a definição de tipo substitui três membros herdados <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, e <xref:System.Object.ToString%2A>.</span><span class="sxs-lookup"><span data-stu-id="8c6bb-111">If an anonymous type declaration contains at least one key property, the type definition overrides three members inherited from <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="8c6bb-112">Se nenhuma propriedade de chave é declarada, apenas <xref:System.Object.ToString%2A> é substituído.</span><span class="sxs-lookup"><span data-stu-id="8c6bb-112">If no key properties are declared, only <xref:System.Object.ToString%2A> is overridden.</span></span> <span data-ttu-id="8c6bb-113">As substituições fornecem a seguinte funcionalidade:</span><span class="sxs-lookup"><span data-stu-id="8c6bb-113">The overrides provide the following functionality:</span></span>  
  
-   <span data-ttu-id="8c6bb-114">`Equals` Retorna `True` se duas instâncias de tipo anônimo são a mesma instância, ou se eles atendem às seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="8c6bb-114">`Equals` returns `True` if two anonymous type instances are the same instance, or if they meet the following conditions:</span></span>  
  
    -   <span data-ttu-id="8c6bb-115">Eles têm o mesmo número de propriedades.</span><span class="sxs-lookup"><span data-stu-id="8c6bb-115">They have the same number of properties.</span></span>  
  
    -   <span data-ttu-id="8c6bb-116">As propriedades são declaradas na mesma ordem, com os mesmos nomes e os mesmos inferidos tipos.</span><span class="sxs-lookup"><span data-stu-id="8c6bb-116">The properties are declared in the same order, with the same names and the same inferred types.</span></span> <span data-ttu-id="8c6bb-117">Comparações de nome não diferenciam maiusculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="8c6bb-117">Name comparisons are not case-sensitive.</span></span>  
  
    -   <span data-ttu-id="8c6bb-118">Pelo menos uma das propriedades é uma propriedade de chave e o `Key` palavra-chave é aplicada às mesmas propriedades.</span><span class="sxs-lookup"><span data-stu-id="8c6bb-118">At least one of the properties is a key property, and the `Key` keyword is applied to the same properties.</span></span>  
  
    -   <span data-ttu-id="8c6bb-119">Comparação entre cada par correspondente de propriedades de chave retorna `True`.</span><span class="sxs-lookup"><span data-stu-id="8c6bb-119">Comparison of each corresponding pair of key properties returns `True`.</span></span>  
  
     <span data-ttu-id="8c6bb-120">Por exemplo, nos exemplos a seguir, `Equals` retorna `True` apenas para `employee01` e `employee08`.</span><span class="sxs-lookup"><span data-stu-id="8c6bb-120">For example, in the following examples, `Equals` returns `True` only for `employee01` and `employee08`.</span></span> <span data-ttu-id="8c6bb-121">O comentário antes de cada linha especifica o motivo por que a nova instância não coincide com `employee01`.</span><span class="sxs-lookup"><span data-stu-id="8c6bb-121">The comment before each line specifies the reason why the new instance does not match `employee01`.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#24)]  
  
-   <span data-ttu-id="8c6bb-122">`GetHashcode` Fornece um algoritmo GetHashCode adequadamente exclusivo.</span><span class="sxs-lookup"><span data-stu-id="8c6bb-122">`GetHashcode` provides an appropriately unique GetHashCode algorithm.</span></span> <span data-ttu-id="8c6bb-123">O algoritmo usa somente as propriedades de chave para calcular o código hash.</span><span class="sxs-lookup"><span data-stu-id="8c6bb-123">The algorithm uses only the key properties to compute the hash code.</span></span>  
  
-   <span data-ttu-id="8c6bb-124">`ToString` Retorna uma cadeia de caracteres concatenada de valores de propriedade, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="8c6bb-124">`ToString` returns a string of concatenated property values, as shown in the following example.</span></span> <span data-ttu-id="8c6bb-125">Chave e propriedades não chave são incluídas.</span><span class="sxs-lookup"><span data-stu-id="8c6bb-125">Both key and non-key properties are included.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#29)]  
  
 <span data-ttu-id="8c6bb-126">Propriedades explicitamente nomeadas de um tipo anônimo não podem entrar em conflito com esses métodos gerados.</span><span class="sxs-lookup"><span data-stu-id="8c6bb-126">Explicitly named properties of an anonymous type cannot conflict with these generated methods.</span></span> <span data-ttu-id="8c6bb-127">Ou seja, você não pode usar `.Equals`, `.GetHashCode`, ou `.ToString` para uma propriedade de nome.</span><span class="sxs-lookup"><span data-stu-id="8c6bb-127">That is, you cannot use `.Equals`, `.GetHashCode`, or `.ToString` to name a property.</span></span>  
  
 <span data-ttu-id="8c6bb-128">Definições de tipo anônimo que incluem pelo menos uma propriedade de chave também implementa o <xref:System.IEquatable%601?displayProperty=nameWithType> interface, onde `T` é o tipo do tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="8c6bb-128">Anonymous type definitions that include at least one key property also implement the <xref:System.IEquatable%601?displayProperty=nameWithType> interface, where `T` is the type of the anonymous type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8c6bb-129">Declarações de tipo anônimo criar o mesmo tipo anônimo somente se ocorrerem no mesmo assembly, suas propriedades têm os mesmos nomes e os mesmos inferidos tipos, as propriedades são declaradas na mesma ordem e as mesmas propriedades são marcadas como propriedades de chave.</span><span class="sxs-lookup"><span data-stu-id="8c6bb-129">Anonymous type declarations create the same anonymous type only if they occur in the same assembly, their properties have the same names and the same inferred types, the properties are declared in the same order, and the same properties are marked as key properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c6bb-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8c6bb-130">See also</span></span>

- [<span data-ttu-id="8c6bb-131">Tipos Anônimos</span><span class="sxs-lookup"><span data-stu-id="8c6bb-131">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="8c6bb-132">Como: Inferir nomes de propriedade e tipos em declarações de tipo anônimo</span><span class="sxs-lookup"><span data-stu-id="8c6bb-132">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
