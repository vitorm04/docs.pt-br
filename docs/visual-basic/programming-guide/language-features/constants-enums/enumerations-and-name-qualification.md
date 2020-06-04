---
title: Enumerações e qualificação de nome
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
ms.openlocfilehash: 4b09284b8282c481e406050d37cbdb2f3c8686bc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414499"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a><span data-ttu-id="e8e4d-102">Enumerações e qualificação de nome (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8e4d-102">Enumerations and Name Qualification (Visual Basic)</span></span>
<span data-ttu-id="e8e4d-103">Normalmente, ao fazer referência a um membro de uma enumeração, você deve qualificar o nome do membro com o nome da enumeração.</span><span class="sxs-lookup"><span data-stu-id="e8e4d-103">Normally, when referring to a member of an enumeration, you must qualify the member name with the enumeration name.</span></span> <span data-ttu-id="e8e4d-104">Por exemplo, para se referir ao `Sunday` membro da sua `Days` enumeração, você usaria a seguinte sintaxe:</span><span class="sxs-lookup"><span data-stu-id="e8e4d-104">For example, to refer to the `Sunday` member of your `Days` enumeration, you would use the following syntax:</span></span>  
  
 [!code-vb[VbEnumsTask#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#18)]  
  
## <a name="using-the-imports-statement"></a><span data-ttu-id="e8e4d-105">Usando a instrução Imports</span><span class="sxs-lookup"><span data-stu-id="e8e4d-105">Using the Imports Statement</span></span>  
 <span data-ttu-id="e8e4d-106">Você pode evitar o uso de nomes totalmente qualificados adicionando uma `Imports` instrução à seção de declarações de namespace do seu código, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="e8e4d-106">You can avoid using fully qualified names by adding an `Imports` statement to the namespace declarations section of your code, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 <span data-ttu-id="e8e4d-107">Uma `Imports` instrução importa nomes de namespace de projetos e assemblies referenciados e de dentro do mesmo projeto que o módulo no qual a instrução é exibida.</span><span class="sxs-lookup"><span data-stu-id="e8e4d-107">An `Imports` statement imports namespace names from referenced projects and assemblies and from within the same project as the module in which the statement appears.</span></span> <span data-ttu-id="e8e4d-108">Depois que essa instrução for adicionada, você poderá consultar seus membros de enumeração sem qualificação, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="e8e4d-108">Once this statement is added, you can refer to your enumeration members without qualification, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#24)]  
  
 <span data-ttu-id="e8e4d-109">Ao organizar conjuntos de constantes relacionadas em enumerações, você pode usar os mesmos nomes de constantes em diferentes contextos.</span><span class="sxs-lookup"><span data-stu-id="e8e4d-109">By organizing sets of related constants in enumerations, you can use the same constant names in different contexts.</span></span> <span data-ttu-id="e8e4d-110">Por exemplo, você pode usar os mesmos nomes para as constantes do dia da semana nas `Days` `WorkDays` enumerações e.</span><span class="sxs-lookup"><span data-stu-id="e8e4d-110">For example, you can use the same names for the weekday constants in the `Days` and `WorkDays` enumerations.</span></span> <span data-ttu-id="e8e4d-111">Se você usar a `Imports` instrução com suas enumerações, deverá ter cuidado para evitar referências ambíguas.</span><span class="sxs-lookup"><span data-stu-id="e8e4d-111">If you use the `Imports` statement with your enumerations, you must be careful to avoid ambiguous references.</span></span> <span data-ttu-id="e8e4d-112">Considere o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="e8e4d-112">Consider the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 [!code-vb[VbEnumsTask#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#25)]  
  
 <span data-ttu-id="e8e4d-113">Supondo que `Monday` seja um membro da `Days` enumeração e da `Workdays` enumeração, esse código gera um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="e8e4d-113">Assuming that `Monday` is a member of both the `Days` enumeration and the `Workdays` enumeration, this code generates a compiler error.</span></span> <span data-ttu-id="e8e4d-114">Para evitar referências ambíguas ao fazer referência a uma constante individual, qualifique o nome da constante com sua enumeração.</span><span class="sxs-lookup"><span data-stu-id="e8e4d-114">To avoid ambiguous references when referring to an individual constant, qualify the constant name with its enumeration.</span></span> <span data-ttu-id="e8e4d-115">O código a seguir refere-se às `Saturday` constantes `Days` nas `WorkDays` enumerações e.</span><span class="sxs-lookup"><span data-stu-id="e8e4d-115">The following code refers to the `Saturday` constants in the `Days` and `WorkDays` enumerations.</span></span>  
  
 [!code-vb[VbEnumsTask#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="e8e4d-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="e8e4d-116">See also</span></span>

- [<span data-ttu-id="e8e4d-117">Constantes e enumerações</span><span class="sxs-lookup"><span data-stu-id="e8e4d-117">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="e8e4d-118">Como declarar uma enumeração</span><span class="sxs-lookup"><span data-stu-id="e8e4d-118">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="e8e4d-119">Como fazer referência a um membro de enumeração</span><span class="sxs-lookup"><span data-stu-id="e8e4d-119">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="e8e4d-120">Como iterar em uma enumeração no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e8e4d-120">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="e8e4d-121">Como determinar a cadeia de caracteres associada a um valor de enumeração</span><span class="sxs-lookup"><span data-stu-id="e8e4d-121">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="e8e4d-122">Quando usar uma enumeração</span><span class="sxs-lookup"><span data-stu-id="e8e4d-122">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="e8e4d-123">Tipos de dados constante e literal</span><span class="sxs-lookup"><span data-stu-id="e8e4d-123">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="e8e4d-124">Instrução Enum</span><span class="sxs-lookup"><span data-stu-id="e8e4d-124">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
- [<span data-ttu-id="e8e4d-125">Instrução Imports (tipo e namespace .NET)</span><span class="sxs-lookup"><span data-stu-id="e8e4d-125">Imports Statement (.NET Namespace and Type)</span></span>](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="e8e4d-126">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="e8e4d-126">Data Types</span></span>](../../../language-reference/data-types/index.md)
