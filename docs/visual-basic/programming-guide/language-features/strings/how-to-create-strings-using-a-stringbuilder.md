---
title: 'Como: Criar cadeias de caracteres usando StringBuilder no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: dec1afdbd3ca6c0ba719a95906de8cf6fc7ba378
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/05/2019
ms.locfileid: "55738793"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="21d5c-102">Como: Criar cadeias de caracteres usando StringBuilder no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="21d5c-102">How to: Create Strings Using a StringBuilder in Visual Basic</span></span>
<span data-ttu-id="21d5c-103">Esse exemplo constrói uma cadeia de caracteres de várias cadeias menores utilizando o <xref:System.Text.StringBuilder> classe.</span><span class="sxs-lookup"><span data-stu-id="21d5c-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="21d5c-104">O <xref:System.Text.StringBuilder> classe é mais eficiente do que o `&=` operador para concatenar várias cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="21d5c-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21d5c-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="21d5c-105">Example</span></span>  
 <span data-ttu-id="21d5c-106">O exemplo a seguir cria uma instância da <xref:System.Text.StringBuilder> classe, anexa 1.000 cadeias de caracteres a essa instância e, em seguida, retorna sua representação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="21d5c-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation.</span></span>  
  
 [!code-vb[VbVbalrStrings#70](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-strings-using-a-stringbuilder_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="21d5c-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21d5c-107">See also</span></span>
- [<span data-ttu-id="21d5c-108">Uso da classe StringBuilder</span><span class="sxs-lookup"><span data-stu-id="21d5c-108">Using the StringBuilder Class</span></span>](../../../../standard/base-types/stringbuilder.md)
- [<span data-ttu-id="21d5c-109">Operador &=</span><span class="sxs-lookup"><span data-stu-id="21d5c-109">&= Operator</span></span>](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="21d5c-110">Cadeias de Caracteres</span><span class="sxs-lookup"><span data-stu-id="21d5c-110">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
- [<span data-ttu-id="21d5c-111">Criando novas cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="21d5c-111">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="21d5c-112">Manipulando cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="21d5c-112">Manipulating Strings</span></span>](../../../../standard/base-types/manipulating-strings.md)
