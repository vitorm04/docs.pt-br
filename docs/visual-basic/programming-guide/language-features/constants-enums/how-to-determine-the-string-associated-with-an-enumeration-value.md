---
title: Como determinar a cadeia de caracteres associada a um valor de enumeração
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: 4138759bfbb049b77406fc536219b40d3ed9e2a5
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058763"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a><span data-ttu-id="38c6b-102">Como determinar a cadeia de caracteres associada a um valor de enumeração (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38c6b-102">How to: Determine the String Associated with an Enumeration Value (Visual Basic)</span></span>

<span data-ttu-id="38c6b-103">Os <xref:System.Enum.GetValues%2A> <xref:System.Enum.GetNames%2A> métodos e permitem que você determine as cadeias de caracteres e os valores associados aos membros da enumeração.</span><span class="sxs-lookup"><span data-stu-id="38c6b-103">The <xref:System.Enum.GetValues%2A> and <xref:System.Enum.GetNames%2A> methods allow you to determine the strings and values associated with enumeration members.</span></span>  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a><span data-ttu-id="38c6b-104">Para determinar a cadeia de caracteres associada a uma enumeração</span><span class="sxs-lookup"><span data-stu-id="38c6b-104">To determine the string associated with an enumeration</span></span>  
  
- <span data-ttu-id="38c6b-105">Use o <xref:System.Enum.GetNames%2A> método para recuperar as cadeias de caracteres associadas aos membros da enumeração.</span><span class="sxs-lookup"><span data-stu-id="38c6b-105">Use the <xref:System.Enum.GetNames%2A> method to retrieve the strings associated with the enumeration members.</span></span> <span data-ttu-id="38c6b-106">Este exemplo declara uma enumeração, e, `flavorEnum` em seguida, usa o <xref:System.Enum.GetNames%2A> método para exibir as cadeias de caracteres associadas a cada membro.</span><span class="sxs-lookup"><span data-stu-id="38c6b-106">This example declares an enumeration, `flavorEnum`, then uses the <xref:System.Enum.GetNames%2A> method to display the strings associated with each member.</span></span>  
  
     [!code-vb[VbEnumsTask#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="38c6b-107">Confira também</span><span class="sxs-lookup"><span data-stu-id="38c6b-107">See also</span></span>

- <xref:System.Enum.GetValues%2A>
- <xref:System.Enum.GetNames%2A>
- <xref:System.Enum>
- [<span data-ttu-id="38c6b-108">Como declarar uma enumeração</span><span class="sxs-lookup"><span data-stu-id="38c6b-108">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="38c6b-109">Como fazer referência a um membro de enumeração</span><span class="sxs-lookup"><span data-stu-id="38c6b-109">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="38c6b-110">Enumerações e qualificação de nome</span><span class="sxs-lookup"><span data-stu-id="38c6b-110">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="38c6b-111">Como iterar em uma enumeração no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="38c6b-111">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="38c6b-112">Quando usar uma enumeração</span><span class="sxs-lookup"><span data-stu-id="38c6b-112">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="38c6b-113">Instrução Enum</span><span class="sxs-lookup"><span data-stu-id="38c6b-113">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
