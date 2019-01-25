---
title: 'Como: Criar cadeias de caracteres usando StringBuilder no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: 84f0f41cf8ee23466d47dae3b1068c3bc5334072
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528440"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="0be6e-102">Como: Criar cadeias de caracteres usando StringBuilder no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0be6e-102">How to: Create Strings Using a StringBuilder in Visual Basic</span></span>
<span data-ttu-id="0be6e-103">Esse exemplo constrói uma cadeia de caracteres de várias cadeias menores utilizando o <xref:System.Text.StringBuilder> classe.</span><span class="sxs-lookup"><span data-stu-id="0be6e-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="0be6e-104">O <xref:System.Text.StringBuilder> classe é mais eficiente do que o `&=` operador para concatenar várias cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="0be6e-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0be6e-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0be6e-105">Example</span></span>  
 <span data-ttu-id="0be6e-106">O exemplo a seguir cria uma instância da <xref:System.Text.StringBuilder> classe, anexa 1.000 cadeias de caracteres a essa instância e, em seguida, retorna sua representação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="0be6e-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation.</span></span>  
  
 [!code-vb[VbVbalrStrings#70](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-strings-using-a-stringbuilder_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0be6e-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0be6e-107">See also</span></span>
- [<span data-ttu-id="0be6e-108">Uso da classe StringBuilder</span><span class="sxs-lookup"><span data-stu-id="0be6e-108">Using the StringBuilder Class</span></span>](../../../../standard/base-types/stringbuilder.md)
- [<span data-ttu-id="0be6e-109">Operador &=</span><span class="sxs-lookup"><span data-stu-id="0be6e-109">&= Operator</span></span>](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="0be6e-110">Cadeias de Caracteres</span><span class="sxs-lookup"><span data-stu-id="0be6e-110">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
- [<span data-ttu-id="0be6e-111">Criando novas cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="0be6e-111">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="0be6e-112">Manipulando cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="0be6e-112">Manipulating Strings</span></span>](../../../../standard/base-types/manipulating-strings.md)
- <span data-ttu-id="0be6e-113">[Exemplo de cadeias de caracteres](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0be6e-113">[Strings Sample](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))</span></span>
