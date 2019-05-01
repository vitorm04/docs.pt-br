---
title: 'Como: Criar cadeias de caracteres usando StringBuilder no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: 00fefcc138164288d872cd339f165dc6ffc0131a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032117"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="c8d31-102">Como: Criar cadeias de caracteres usando StringBuilder no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c8d31-102">How to: Create Strings Using a StringBuilder in Visual Basic</span></span>
<span data-ttu-id="c8d31-103">Esse exemplo constrói uma cadeia de caracteres de várias cadeias menores utilizando o <xref:System.Text.StringBuilder> classe.</span><span class="sxs-lookup"><span data-stu-id="c8d31-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="c8d31-104">O <xref:System.Text.StringBuilder> classe é mais eficiente do que o `&=` operador para concatenar várias cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c8d31-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8d31-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c8d31-105">Example</span></span>  
 <span data-ttu-id="c8d31-106">O exemplo a seguir cria uma instância da <xref:System.Text.StringBuilder> classe, anexa 1.000 cadeias de caracteres a essa instância e, em seguida, retorna sua representação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c8d31-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation.</span></span>  
  
 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]  
  
## <a name="see-also"></a><span data-ttu-id="c8d31-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c8d31-107">See also</span></span>

- [<span data-ttu-id="c8d31-108">Uso da classe StringBuilder</span><span class="sxs-lookup"><span data-stu-id="c8d31-108">Using the StringBuilder Class</span></span>](../../../../standard/base-types/stringbuilder.md)
- [<span data-ttu-id="c8d31-109">Operador &=</span><span class="sxs-lookup"><span data-stu-id="c8d31-109">&= Operator</span></span>](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="c8d31-110">Cadeias de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c8d31-110">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
- [<span data-ttu-id="c8d31-111">Criando novas cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="c8d31-111">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="c8d31-112">Manipulando cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="c8d31-112">Manipulating Strings</span></span>](../../../../standard/base-types/manipulating-strings.md)
