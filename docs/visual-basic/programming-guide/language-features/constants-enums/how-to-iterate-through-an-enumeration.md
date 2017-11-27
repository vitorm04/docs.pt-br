---
title: "Como iterar em uma enumeração no Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 439e6eae7d475316625a2cc1d3a70a9e7181f68a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a><span data-ttu-id="6d9a7-102">Como iterar em uma enumeração no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6d9a7-102">How to: Iterate Through An Enumeration in Visual Basic</span></span>
<span data-ttu-id="6d9a7-103">Enumerações fornecem uma maneira conveniente para trabalhar com conjuntos de constantes relacionadas e para associar valores de constante a nomes.</span><span class="sxs-lookup"><span data-stu-id="6d9a7-103">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="6d9a7-104">Para iterar por meio de uma enumeração, você pode movê-la em uma matriz usando o <xref:System.Enum.GetValues%2A> método.</span><span class="sxs-lookup"><span data-stu-id="6d9a7-104">To iterate through an enumeration, you can move it into an array using the <xref:System.Enum.GetValues%2A> method.</span></span> <span data-ttu-id="6d9a7-105">Você também pode iterar por meio de uma enumeração usando um `For...Each` instrução, usando o <xref:System.Enum.GetNames%2A> ou <xref:System.Enum.GetValues%2A> método para extrair o valor de cadeia de caracteres ou numérica.</span><span class="sxs-lookup"><span data-stu-id="6d9a7-105">You could also iterate through an enumeration using a `For...Each` statement, using the <xref:System.Enum.GetNames%2A> or <xref:System.Enum.GetValues%2A> method to extract the string or numeric value.</span></span>  
  
### <a name="to-iterate-through-an-enumeration"></a><span data-ttu-id="6d9a7-106">Para iterar por meio de uma enumeração</span><span class="sxs-lookup"><span data-stu-id="6d9a7-106">To iterate through an enumeration</span></span>  
  
-   <span data-ttu-id="6d9a7-107">Declara uma matriz e converter a enumeração com o <xref:System.Enum.GetValues%2A> método antes de passar a matriz como você faria qualquer outra variável.</span><span class="sxs-lookup"><span data-stu-id="6d9a7-107">Declare an array and convert the enumeration to it with the <xref:System.Enum.GetValues%2A> method before passing the array as you would any other variable.</span></span> <span data-ttu-id="6d9a7-108">O exemplo a seguir exibe cada membro da enumeração <xref:Microsoft.VisualBasic.FirstDayOfWeek> como ele itera por meio de enumeração.</span><span class="sxs-lookup"><span data-stu-id="6d9a7-108">The following example displays each member of the enumeration <xref:Microsoft.VisualBasic.FirstDayOfWeek> as it iterates through the enumeration.</span></span>  
  
     [!code-vb[VbEnumsTask#7](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-iterate-through-an-enumeration_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="6d9a7-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d9a7-109">See Also</span></span>  
 [<span data-ttu-id="6d9a7-110">Visão geral de Enumerações</span><span class="sxs-lookup"><span data-stu-id="6d9a7-110">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [<span data-ttu-id="6d9a7-111">Como: declarar uma enumeração</span><span class="sxs-lookup"><span data-stu-id="6d9a7-111">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="6d9a7-112">Quando Usar uma Enumeração</span><span class="sxs-lookup"><span data-stu-id="6d9a7-112">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [<span data-ttu-id="6d9a7-113">Como determinar a cadeia de caracteres associada a um valor de enumeração</span><span class="sxs-lookup"><span data-stu-id="6d9a7-113">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [<span data-ttu-id="6d9a7-114">Como fazer referência a um membro de enumeração</span><span class="sxs-lookup"><span data-stu-id="6d9a7-114">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="6d9a7-115">Enumerações e Qualificação de Nome</span><span class="sxs-lookup"><span data-stu-id="6d9a7-115">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="6d9a7-116">Matrizes</span><span class="sxs-lookup"><span data-stu-id="6d9a7-116">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
