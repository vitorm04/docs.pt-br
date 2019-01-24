---
title: 'Como: Iterar por meio de uma enumeração no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: 4c2ff10fc038ca981fc85c99ba6cf762383d5d7e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54571958"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a><span data-ttu-id="05c1d-102">Como: Iterar por meio de uma enumeração no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="05c1d-102">How to: Iterate Through An Enumeration in Visual Basic</span></span>
<span data-ttu-id="05c1d-103">Enumerações fornecem uma maneira conveniente para trabalhar com conjuntos de constantes relacionadas e para associar valores de constante a nomes.</span><span class="sxs-lookup"><span data-stu-id="05c1d-103">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="05c1d-104">Para iterar por meio de uma enumeração, você pode movê-lo em uma matriz usando o <xref:System.Enum.GetValues%2A> método.</span><span class="sxs-lookup"><span data-stu-id="05c1d-104">To iterate through an enumeration, you can move it into an array using the <xref:System.Enum.GetValues%2A> method.</span></span> <span data-ttu-id="05c1d-105">Você também pode iterar por meio de uma enumeração usando um `For...Each` instrução, usando o <xref:System.Enum.GetNames%2A> ou <xref:System.Enum.GetValues%2A> método para extrair o valor de cadeia de caracteres ou numérica.</span><span class="sxs-lookup"><span data-stu-id="05c1d-105">You could also iterate through an enumeration using a `For...Each` statement, using the <xref:System.Enum.GetNames%2A> or <xref:System.Enum.GetValues%2A> method to extract the string or numeric value.</span></span>  
  
### <a name="to-iterate-through-an-enumeration"></a><span data-ttu-id="05c1d-106">Para iterar por meio de uma enumeração</span><span class="sxs-lookup"><span data-stu-id="05c1d-106">To iterate through an enumeration</span></span>  
  
-   <span data-ttu-id="05c1d-107">Declarar uma matriz e converter a enumeração a ele com o <xref:System.Enum.GetValues%2A> método antes de passar a matriz como você faria qualquer outra variável.</span><span class="sxs-lookup"><span data-stu-id="05c1d-107">Declare an array and convert the enumeration to it with the <xref:System.Enum.GetValues%2A> method before passing the array as you would any other variable.</span></span> <span data-ttu-id="05c1d-108">O exemplo a seguir exibe cada membro da enumeração <xref:Microsoft.VisualBasic.FirstDayOfWeek> conforme ela itera por meio da enumeração.</span><span class="sxs-lookup"><span data-stu-id="05c1d-108">The following example displays each member of the enumeration <xref:Microsoft.VisualBasic.FirstDayOfWeek> as it iterates through the enumeration.</span></span>  
  
     [!code-vb[VbEnumsTask#7](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-iterate-through-an-enumeration_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="05c1d-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="05c1d-109">See also</span></span>
- [<span data-ttu-id="05c1d-110">Visão geral de Enumerações</span><span class="sxs-lookup"><span data-stu-id="05c1d-110">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [<span data-ttu-id="05c1d-111">Como: Declarar uma enumeração</span><span class="sxs-lookup"><span data-stu-id="05c1d-111">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="05c1d-112">Quando Usar uma Enumeração</span><span class="sxs-lookup"><span data-stu-id="05c1d-112">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="05c1d-113">Como: Determinar a cadeia de caracteres associada a um valor de enumeração</span><span class="sxs-lookup"><span data-stu-id="05c1d-113">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="05c1d-114">Como: Fazer referência a um membro de enumeração</span><span class="sxs-lookup"><span data-stu-id="05c1d-114">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="05c1d-115">Enumerações e Qualificação de Nome</span><span class="sxs-lookup"><span data-stu-id="05c1d-115">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="05c1d-116">Matrizes</span><span class="sxs-lookup"><span data-stu-id="05c1d-116">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
