---
title: Enumerações e qualificação de nome (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- Imports statement [Visual Basic], namespace declarations
- declaring namespaces [Visual Basic], enumerations
- name collisions
- ambiguous names [Visual Basic], enumerations
- enumerations [Visual Basic], name qualification
- names [Visual Basic], avoiding conflicts
- namespaces [Visual Basic], declaring
- naming conflicts, enumerations
- naming conflicts, qualifying names
- declaring enumerations
- references [Visual Basic], enumeration members
- naming conventions [Visual Basic], naming conflicts
- declarations [Visual Basic], namespaces
ms.assetid: 08ba2738-df52-4140-bc55-f57c871c9b73
ms.openlocfilehash: f0a806b040720cf6682f8a72025a0590dd4d91f7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61907433"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a><span data-ttu-id="f0878-102">Enumerações e qualificação de nome (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f0878-102">Enumerations and Name Qualification (Visual Basic)</span></span>
<span data-ttu-id="f0878-103">Normalmente, ao fazer referência a um membro de uma enumeração, você deve qualificar o nome do membro com o nome de enumeração.</span><span class="sxs-lookup"><span data-stu-id="f0878-103">Normally, when referring to a member of an enumeration, you must qualify the member name with the enumeration name.</span></span> <span data-ttu-id="f0878-104">Por exemplo, para fazer referência a `Sunday` membro do seu `Days` enumeração, você usaria a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="f0878-104">For example, to refer to the `Sunday` member of your `Days` enumeration, you would use the following syntax:</span></span>  
  
 [!code-vb[VbEnumsTask#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#18)]  
  
## <a name="using-the-imports-statement"></a><span data-ttu-id="f0878-105">Usando a instrução Imports</span><span class="sxs-lookup"><span data-stu-id="f0878-105">Using the Imports Statement</span></span>  
 <span data-ttu-id="f0878-106">Você pode evitar o uso de nomes totalmente qualificados, adicionando um `Imports` instrução para a seção de declarações de namespace do seu código, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f0878-106">You can avoid using fully qualified names by adding an `Imports` statement to the namespace declarations section of your code, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 <span data-ttu-id="f0878-107">Um `Imports` instrução importa nomes de namespace de projetos e assemblies referenciados e de dentro do mesmo projeto como o módulo no qual a instrução aparece.</span><span class="sxs-lookup"><span data-stu-id="f0878-107">An `Imports` statement imports namespace names from referenced projects and assemblies and from within the same project as the module in which the statement appears.</span></span> <span data-ttu-id="f0878-108">Depois que essa instrução é adicionada, você pode consultar os membros da enumeração sem qualificação, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f0878-108">Once this statement is added, you can refer to your enumeration members without qualification, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#24)]  
  
 <span data-ttu-id="f0878-109">Organizando conjuntos de constantes relacionadas em enumerações, você pode usar os mesmos nomes de constantes em contextos diferentes.</span><span class="sxs-lookup"><span data-stu-id="f0878-109">By organizing sets of related constants in enumerations, you can use the same constant names in different contexts.</span></span> <span data-ttu-id="f0878-110">Por exemplo, você pode usar os mesmos nomes para as constantes de dia da semana na `Days` e `WorkDays` enumerações.</span><span class="sxs-lookup"><span data-stu-id="f0878-110">For example, you can use the same names for the weekday constants in the `Days` and `WorkDays` enumerations.</span></span> <span data-ttu-id="f0878-111">Se você usar o `Imports` instrução com suas enumerações, tenha cuidado evitar referências ambíguas.</span><span class="sxs-lookup"><span data-stu-id="f0878-111">If you use the `Imports` statement with your enumerations, you must be careful to avoid ambiguous references.</span></span> <span data-ttu-id="f0878-112">Considere o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f0878-112">Consider the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 [!code-vb[VbEnumsTask#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#25)]  
  
 <span data-ttu-id="f0878-113">Supondo que `Monday` é um membro de ambos os `Days` enumeração e a `Workdays` enumeração, esse código gera um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="f0878-113">Assuming that `Monday` is a member of both the `Days` enumeration and the `Workdays` enumeration, this code generates a compiler error.</span></span> <span data-ttu-id="f0878-114">Para evitar referências ambíguas para se referir a uma constante individual, qualifica o nome de constante com sua enumeração.</span><span class="sxs-lookup"><span data-stu-id="f0878-114">To avoid ambiguous references when referring to an individual constant, qualify the constant name with its enumeration.</span></span> <span data-ttu-id="f0878-115">O código a seguir refere-se para o `Saturday` constantes em de `Days` e `WorkDays` enumerações.</span><span class="sxs-lookup"><span data-stu-id="f0878-115">The following code refers to the `Saturday` constants in the `Days` and `WorkDays` enumerations.</span></span>  
  
 [!code-vb[VbEnumsTask#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="f0878-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f0878-116">See also</span></span>

- [<span data-ttu-id="f0878-117">Constantes e Enumerações</span><span class="sxs-lookup"><span data-stu-id="f0878-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="f0878-118">Como: Declarar uma enumeração</span><span class="sxs-lookup"><span data-stu-id="f0878-118">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="f0878-119">Como: Fazer referência a um membro de enumeração</span><span class="sxs-lookup"><span data-stu-id="f0878-119">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="f0878-120">Como: Iterar por meio de uma enumeração no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f0878-120">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="f0878-121">Como: Determinar a cadeia de caracteres associada a um valor de enumeração</span><span class="sxs-lookup"><span data-stu-id="f0878-121">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="f0878-122">Quando Usar uma Enumeração</span><span class="sxs-lookup"><span data-stu-id="f0878-122">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="f0878-123">Tipos de Dados Constante e Literal</span><span class="sxs-lookup"><span data-stu-id="f0878-123">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [<span data-ttu-id="f0878-124">Instrução Enum</span><span class="sxs-lookup"><span data-stu-id="f0878-124">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [<span data-ttu-id="f0878-125">Instrução Imports (Tipo e Namespace .NET)</span><span class="sxs-lookup"><span data-stu-id="f0878-125">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="f0878-126">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="f0878-126">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
