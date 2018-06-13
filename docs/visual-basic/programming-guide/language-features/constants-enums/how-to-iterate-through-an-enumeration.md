---
title: Como iterar em uma enumeração no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: 06609d38c805e5f073a2f3a299ecc3aa7cf7be01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646572"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a><span data-ttu-id="0962f-102">Como iterar em uma enumeração no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0962f-102">How to: Iterate Through An Enumeration in Visual Basic</span></span>
<span data-ttu-id="0962f-103">Enumerações fornecem uma maneira conveniente para trabalhar com conjuntos de constantes relacionadas e para associar valores de constante a nomes.</span><span class="sxs-lookup"><span data-stu-id="0962f-103">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="0962f-104">Para iterar por meio de uma enumeração, você pode movê-la em uma matriz usando o <xref:System.Enum.GetValues%2A> método.</span><span class="sxs-lookup"><span data-stu-id="0962f-104">To iterate through an enumeration, you can move it into an array using the <xref:System.Enum.GetValues%2A> method.</span></span> <span data-ttu-id="0962f-105">Você também pode iterar por meio de uma enumeração usando um `For...Each` instrução, usando o <xref:System.Enum.GetNames%2A> ou <xref:System.Enum.GetValues%2A> método para extrair o valor de cadeia de caracteres ou numérica.</span><span class="sxs-lookup"><span data-stu-id="0962f-105">You could also iterate through an enumeration using a `For...Each` statement, using the <xref:System.Enum.GetNames%2A> or <xref:System.Enum.GetValues%2A> method to extract the string or numeric value.</span></span>  
  
### <a name="to-iterate-through-an-enumeration"></a><span data-ttu-id="0962f-106">Para iterar por meio de uma enumeração</span><span class="sxs-lookup"><span data-stu-id="0962f-106">To iterate through an enumeration</span></span>  
  
-   <span data-ttu-id="0962f-107">Declara uma matriz e converter a enumeração com o <xref:System.Enum.GetValues%2A> método antes de passar a matriz como você faria qualquer outra variável.</span><span class="sxs-lookup"><span data-stu-id="0962f-107">Declare an array and convert the enumeration to it with the <xref:System.Enum.GetValues%2A> method before passing the array as you would any other variable.</span></span> <span data-ttu-id="0962f-108">O exemplo a seguir exibe cada membro da enumeração <xref:Microsoft.VisualBasic.FirstDayOfWeek> como ele itera por meio de enumeração.</span><span class="sxs-lookup"><span data-stu-id="0962f-108">The following example displays each member of the enumeration <xref:Microsoft.VisualBasic.FirstDayOfWeek> as it iterates through the enumeration.</span></span>  
  
     [!code-vb[VbEnumsTask#7](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-iterate-through-an-enumeration_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0962f-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0962f-109">See Also</span></span>  
 [<span data-ttu-id="0962f-110">Visão geral de Enumerações</span><span class="sxs-lookup"><span data-stu-id="0962f-110">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [<span data-ttu-id="0962f-111">Como: declarar uma enumeração</span><span class="sxs-lookup"><span data-stu-id="0962f-111">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="0962f-112">Quando Usar uma Enumeração</span><span class="sxs-lookup"><span data-stu-id="0962f-112">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [<span data-ttu-id="0962f-113">Como determinar a cadeia de caracteres associada a um valor de enumeração</span><span class="sxs-lookup"><span data-stu-id="0962f-113">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [<span data-ttu-id="0962f-114">Como fazer referência a um membro de enumeração</span><span class="sxs-lookup"><span data-stu-id="0962f-114">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="0962f-115">Enumerações e Qualificação de Nome</span><span class="sxs-lookup"><span data-stu-id="0962f-115">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="0962f-116">Matrizes</span><span class="sxs-lookup"><span data-stu-id="0962f-116">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
