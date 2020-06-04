---
title: Como iterar em uma enumeração
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: fb6fbdd45ca0e84ccb9fc55296d78e3867d5fe25
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414421"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a><span data-ttu-id="b0efc-102">Como iterar em uma enumeração no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b0efc-102">How to: Iterate Through An Enumeration in Visual Basic</span></span>
<span data-ttu-id="b0efc-103">Enumerações fornecem uma maneira conveniente para trabalhar com conjuntos de constantes relacionadas e para associar valores de constante a nomes.</span><span class="sxs-lookup"><span data-stu-id="b0efc-103">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="b0efc-104">Para iterar por meio de uma enumeração, você pode movê-lo para uma matriz usando o <xref:System.Enum.GetValues%2A> método.</span><span class="sxs-lookup"><span data-stu-id="b0efc-104">To iterate through an enumeration, you can move it into an array using the <xref:System.Enum.GetValues%2A> method.</span></span> <span data-ttu-id="b0efc-105">Você também pode iterar por meio de uma enumeração usando uma `For...Each` instrução, usando o <xref:System.Enum.GetNames%2A> <xref:System.Enum.GetValues%2A> método ou para extrair a cadeia de caracteres ou o valor numérico.</span><span class="sxs-lookup"><span data-stu-id="b0efc-105">You could also iterate through an enumeration using a `For...Each` statement, using the <xref:System.Enum.GetNames%2A> or <xref:System.Enum.GetValues%2A> method to extract the string or numeric value.</span></span>  
  
### <a name="to-iterate-through-an-enumeration"></a><span data-ttu-id="b0efc-106">Para iterar por meio de uma enumeração</span><span class="sxs-lookup"><span data-stu-id="b0efc-106">To iterate through an enumeration</span></span>  
  
- <span data-ttu-id="b0efc-107">Declare uma matriz e converta a enumeração para ela com o <xref:System.Enum.GetValues%2A> método antes de passar a matriz, como faria com qualquer outra variável.</span><span class="sxs-lookup"><span data-stu-id="b0efc-107">Declare an array and convert the enumeration to it with the <xref:System.Enum.GetValues%2A> method before passing the array as you would any other variable.</span></span> <span data-ttu-id="b0efc-108">O exemplo a seguir exibe cada membro da enumeração <xref:Microsoft.VisualBasic.FirstDayOfWeek> à medida que ele é iterado pela enumeração.</span><span class="sxs-lookup"><span data-stu-id="b0efc-108">The following example displays each member of the enumeration <xref:Microsoft.VisualBasic.FirstDayOfWeek> as it iterates through the enumeration.</span></span>  
  
     [!code-vb[VbEnumsTask#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="b0efc-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="b0efc-109">See also</span></span>

- [<span data-ttu-id="b0efc-110">Visão geral de enumerações</span><span class="sxs-lookup"><span data-stu-id="b0efc-110">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="b0efc-111">Como declarar uma enumeração</span><span class="sxs-lookup"><span data-stu-id="b0efc-111">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="b0efc-112">Quando usar uma enumeração</span><span class="sxs-lookup"><span data-stu-id="b0efc-112">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="b0efc-113">Como determinar a cadeia de caracteres associada a um valor de enumeração</span><span class="sxs-lookup"><span data-stu-id="b0efc-113">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="b0efc-114">Como fazer referência a um membro de enumeração</span><span class="sxs-lookup"><span data-stu-id="b0efc-114">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="b0efc-115">Enumerações e qualificação de nome</span><span class="sxs-lookup"><span data-stu-id="b0efc-115">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="b0efc-116">Matrizes</span><span class="sxs-lookup"><span data-stu-id="b0efc-116">Arrays</span></span>](../arrays/index.md)
