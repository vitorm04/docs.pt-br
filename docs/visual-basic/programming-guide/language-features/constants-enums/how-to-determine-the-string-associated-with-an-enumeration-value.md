---
title: 'Como: Determinar a cadeia de caracteres associada a um valor de enumeração (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: 92d2e9918429c9cf408f288f832e4615b95ad423
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690183"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a><span data-ttu-id="c9d78-102">Como: Determinar a cadeia de caracteres associada a um valor de enumeração (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9d78-102">How to: Determine the String Associated with an Enumeration Value (Visual Basic)</span></span>
<span data-ttu-id="c9d78-103">O <xref:System.Enum.GetValues%2A> e <xref:System.Enum.GetNames%2A> métodos permitem determinar as cadeias de caracteres e valores associados a membros de enumeração.</span><span class="sxs-lookup"><span data-stu-id="c9d78-103">The <xref:System.Enum.GetValues%2A> and <xref:System.Enum.GetNames%2A> methods allow you to determine the strings and values associated with enumeration members.</span></span>  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a><span data-ttu-id="c9d78-104">Para determinar a cadeia de caracteres associada a uma enumeração</span><span class="sxs-lookup"><span data-stu-id="c9d78-104">To determine the string associated with an enumeration</span></span>  
  
-   <span data-ttu-id="c9d78-105">Use o <xref:System.Enum.GetNames%2A> método para recuperar as cadeias de caracteres associadas com os membros de enumeração.</span><span class="sxs-lookup"><span data-stu-id="c9d78-105">Use the <xref:System.Enum.GetNames%2A> method to retrieve the strings associated with the enumeration members.</span></span> <span data-ttu-id="c9d78-106">Este exemplo declara uma enumeração `flavorEnum`, em seguida, usa o <xref:System.Enum.GetNames%2A> método para exibir as cadeias de caracteres associadas a cada membro.</span><span class="sxs-lookup"><span data-stu-id="c9d78-106">This example declares an enumeration, `flavorEnum`, then uses the <xref:System.Enum.GetNames%2A> method to display the strings associated with each member.</span></span>  
  
     [!code-vb[VbEnumsTask#2](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-determine-the-string-associated-with-an-enumeration-value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c9d78-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9d78-107">See also</span></span>
- <xref:System.Enum.GetValues%2A>
- <xref:System.Enum.GetNames%2A>
- <xref:System.Enum>
- [<span data-ttu-id="c9d78-108">Como: Declarar uma enumeração</span><span class="sxs-lookup"><span data-stu-id="c9d78-108">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="c9d78-109">Como: Fazer referência a um membro de enumeração</span><span class="sxs-lookup"><span data-stu-id="c9d78-109">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="c9d78-110">Enumerações e Qualificação de Nome</span><span class="sxs-lookup"><span data-stu-id="c9d78-110">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="c9d78-111">Como: Iterar por meio de uma enumeração no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c9d78-111">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="c9d78-112">Quando Usar uma Enumeração</span><span class="sxs-lookup"><span data-stu-id="c9d78-112">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="c9d78-113">Instrução Enum</span><span class="sxs-lookup"><span data-stu-id="c9d78-113">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)
