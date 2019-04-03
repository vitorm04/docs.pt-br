---
title: 'Como: Criar cadeias de caracteres usando StringBuilder no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: 00fefcc138164288d872cd339f165dc6ffc0131a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834186"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="e9e28-102">Como: Criar cadeias de caracteres usando StringBuilder no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e9e28-102">How to: Create Strings Using a StringBuilder in Visual Basic</span></span>
<span data-ttu-id="e9e28-103">Esse exemplo constrói uma cadeia de caracteres de várias cadeias menores utilizando o <xref:System.Text.StringBuilder> classe.</span><span class="sxs-lookup"><span data-stu-id="e9e28-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="e9e28-104">O <xref:System.Text.StringBuilder> classe é mais eficiente do que o `&=` operador para concatenar várias cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e9e28-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9e28-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e9e28-105">Example</span></span>  
 <span data-ttu-id="e9e28-106">O exemplo a seguir cria uma instância da <xref:System.Text.StringBuilder> classe, anexa 1.000 cadeias de caracteres a essa instância e, em seguida, retorna sua representação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e9e28-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation.</span></span>  
  
 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]  
  
## <a name="see-also"></a><span data-ttu-id="e9e28-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e9e28-107">See also</span></span>

- [<span data-ttu-id="e9e28-108">Uso da classe StringBuilder</span><span class="sxs-lookup"><span data-stu-id="e9e28-108">Using the StringBuilder Class</span></span>](../../../../standard/base-types/stringbuilder.md)
- [<span data-ttu-id="e9e28-109">Operador &=</span><span class="sxs-lookup"><span data-stu-id="e9e28-109">&= Operator</span></span>](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="e9e28-110">Cadeias de Caracteres</span><span class="sxs-lookup"><span data-stu-id="e9e28-110">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
- [<span data-ttu-id="e9e28-111">Criando novas cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="e9e28-111">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="e9e28-112">Manipulando cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="e9e28-112">Manipulating Strings</span></span>](../../../../standard/base-types/manipulating-strings.md)
