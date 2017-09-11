---
title: "Enumerações e qualificação de nome (Visual Basic) | Documentos do Microsoft"
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
- declarations, enumerations
- Imports statement, namespace declarations
- declaring namespaces, enumerations
- name collisions
- ambiguous names, enumerations
- enumerations [Visual Basic], name qualification
- names, avoiding conflicts
- namespaces, declaring
- naming conflicts, enumerations
- naming conflicts, qualifying names
- declaring enumerations
- references, enumeration members
- naming conventions, naming conflicts
- declarations, namespaces
ms.assetid: 08ba2738-df52-4140-bc55-f57c871c9b73
caps.latest.revision: 20
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
ms.openlocfilehash: 8259778bb1dea52bab6676483ad18d967657df09
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="enumerations-and-name-qualification-visual-basic"></a><span data-ttu-id="839b5-102">Enumerações e qualificação de nome (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="839b5-102">Enumerations and Name Qualification (Visual Basic)</span></span>
<span data-ttu-id="839b5-103">Normalmente, ao se referir a um membro de uma enumeração, você deve qualificar o nome do membro com o nome da enumeração.</span><span class="sxs-lookup"><span data-stu-id="839b5-103">Normally, when referring to a member of an enumeration, you must qualify the member name with the enumeration name.</span></span> <span data-ttu-id="839b5-104">Por exemplo, para referir-se a `Sunday` membro do seu `Days` enumeração, você usaria a sintaxe a seguir:</span><span class="sxs-lookup"><span data-stu-id="839b5-104">For example, to refer to the `Sunday` member of your `Days` enumeration, you would use the following syntax:</span></span>  
  
 <span data-ttu-id="839b5-105">[!code-vb[VbEnumsTask n º&18;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="839b5-105">[!code-vb[VbEnumsTask#18](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_1.vb)]</span></span>  
  
## <a name="using-the-imports-statement"></a><span data-ttu-id="839b5-106">Usando a instrução Imports</span><span class="sxs-lookup"><span data-stu-id="839b5-106">Using the Imports Statement</span></span>  
 <span data-ttu-id="839b5-107">Você pode evitar o uso de nomes totalmente qualificados, adicionando uma `Imports` instrução à seção de declarações de namespaces do seu código, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="839b5-107">You can avoid using fully qualified names by adding an `Imports` statement to the namespace declarations section of your code, as in the following example:</span></span>  
  
 <span data-ttu-id="839b5-108">[!code-vb[VbEnumsTask&#22;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="839b5-108">[!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]</span></span>  
  
 <span data-ttu-id="839b5-109">Um `Imports` instrução importa nomes de namespaces de projetos e assemblies referenciados e do mesmo projeto como o módulo no qual a instrução aparece.</span><span class="sxs-lookup"><span data-stu-id="839b5-109">An `Imports` statement imports namespace names from referenced projects and assemblies and from within the same project as the module in which the statement appears.</span></span> <span data-ttu-id="839b5-110">Depois que essa instrução é adicionada, você pode consultar os membros da enumeração sem qualificação, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="839b5-110">Once this statement is added, you can refer to your enumeration members without qualification, as in the following example:</span></span>  
  
 <span data-ttu-id="839b5-111">[!code-vb[VbEnumsTask&#24;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="839b5-111">[!code-vb[VbEnumsTask#24](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_3.vb)]</span></span>  
  
 <span data-ttu-id="839b5-112">Organizando conjuntos de constantes relacionadas em enumerações, você pode usar os mesmos nomes de constantes em contextos diferentes.</span><span class="sxs-lookup"><span data-stu-id="839b5-112">By organizing sets of related constants in enumerations, you can use the same constant names in different contexts.</span></span> <span data-ttu-id="839b5-113">Por exemplo, você pode usar os mesmos nomes para as constantes dias da semana no `Days` e `WorkDays` enumerações.</span><span class="sxs-lookup"><span data-stu-id="839b5-113">For example, you can use the same names for the weekday constants in the `Days` and `WorkDays` enumerations.</span></span> <span data-ttu-id="839b5-114">Se você usar o `Imports` instrução com suas enumerações, você deve ter cuidado para evitar referências ambíguas.</span><span class="sxs-lookup"><span data-stu-id="839b5-114">If you use the `Imports` statement with your enumerations, you must be careful to avoid ambiguous references.</span></span> <span data-ttu-id="839b5-115">Considere o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="839b5-115">Consider the following example:</span></span>  
  
 <span data-ttu-id="839b5-116">[!code-vb[VbEnumsTask&#22;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="839b5-116">[!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]</span></span>  
  
 <span data-ttu-id="839b5-117">[!code-vb[25 VbEnumsTask](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="839b5-117">[!code-vb[VbEnumsTask#25](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_4.vb)]</span></span>  
  
 <span data-ttu-id="839b5-118">Supondo que `Monday` é um membro de ambos os `Days` enumeração e `Workdays` enumeração, esse código gera um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="839b5-118">Assuming that `Monday` is a member of both the `Days` enumeration and the `Workdays` enumeration, this code generates a compiler error.</span></span> <span data-ttu-id="839b5-119">Para evitar referências ambíguas quando se referir a uma constante individual, qualifica o nome constante com sua enumeração.</span><span class="sxs-lookup"><span data-stu-id="839b5-119">To avoid ambiguous references when referring to an individual constant, qualify the constant name with its enumeration.</span></span> <span data-ttu-id="839b5-120">O código a seguir refere-se para o `Saturday` constantes no `Days` e `WorkDays` enumerações.</span><span class="sxs-lookup"><span data-stu-id="839b5-120">The following code refers to the `Saturday` constants in the `Days` and `WorkDays` enumerations.</span></span>  
  
 <span data-ttu-id="839b5-121">[!code-vb[32 VbEnumsTask](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="839b5-121">[!code-vb[VbEnumsTask#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_5.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="839b5-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="839b5-122">See Also</span></span>  
 <span data-ttu-id="839b5-123">[Constantes e enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md) </span><span class="sxs-lookup"><span data-stu-id="839b5-123">[Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md) </span></span>  
<span data-ttu-id="839b5-124"> [Como: declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md) </span><span class="sxs-lookup"><span data-stu-id="839b5-124"> [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md) </span></span>  
<span data-ttu-id="839b5-125"> [Como: fazer referência a um membro de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md) </span><span class="sxs-lookup"><span data-stu-id="839b5-125"> [How to: Refer to an Enumeration Member](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md) </span></span>  
<span data-ttu-id="839b5-126"> [Como: iterar por uma enumeração no Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md) </span><span class="sxs-lookup"><span data-stu-id="839b5-126"> [How to: Iterate Through An Enumeration in Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md) </span></span>  
<span data-ttu-id="839b5-127"> [Como: determinar a cadeia de caracteres associada a um valor de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md) </span><span class="sxs-lookup"><span data-stu-id="839b5-127"> [How to: Determine the String Associated with an Enumeration Value](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md) </span></span>  
<span data-ttu-id="839b5-128"> [Quando usar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md) </span><span class="sxs-lookup"><span data-stu-id="839b5-128"> [When to Use an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md) </span></span>  
<span data-ttu-id="839b5-129"> [Tipos de dados constante e Literal](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="839b5-129"> [Constant and Literal Data Types](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md) </span></span>  
<span data-ttu-id="839b5-130"> [Instrução Enum](../../../../visual-basic/language-reference/statements/enum-statement.md) </span><span class="sxs-lookup"><span data-stu-id="839b5-130"> [Enum Statement](../../../../visual-basic/language-reference/statements/enum-statement.md) </span></span>  
<span data-ttu-id="839b5-131"> [Instrução Imports (tipo e Namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span><span class="sxs-lookup"><span data-stu-id="839b5-131"> [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span></span>  
<span data-ttu-id="839b5-132"> [Tipos de Dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md)</span><span class="sxs-lookup"><span data-stu-id="839b5-132"> [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)</span></span>
