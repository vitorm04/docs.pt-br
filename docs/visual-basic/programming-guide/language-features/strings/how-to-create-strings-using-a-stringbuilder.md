---
title: 'Como: criar strings usando um StringBuilder'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: c41db584df83782dab99b90043045aa2cabcb6ff
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645323"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="d1581-102">Como: criar strings usando um StringBuilder no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d1581-102">How to: create strings using a StringBuilder in Visual Basic</span></span>

<span data-ttu-id="d1581-103">Este exemplo constrói uma longa seqüência de <xref:System.Text.StringBuilder> muitas strings menores usando a classe.</span><span class="sxs-lookup"><span data-stu-id="d1581-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="d1581-104">A <xref:System.Text.StringBuilder> classe é mais `&=` eficiente do que o operador para concatenar muitas cordas.</span><span class="sxs-lookup"><span data-stu-id="d1581-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>

## <a name="example"></a><span data-ttu-id="d1581-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d1581-105">Example</span></span>

<span data-ttu-id="d1581-106">O exemplo a seguir <xref:System.Text.StringBuilder> cria uma instância da classe, anexa 1.000 strings a essa instância e, em seguida, retorna sua representação de strings:</span><span class="sxs-lookup"><span data-stu-id="d1581-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation:</span></span>

 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]

## <a name="see-also"></a><span data-ttu-id="d1581-107">Confira também</span><span class="sxs-lookup"><span data-stu-id="d1581-107">See also</span></span>

- [<span data-ttu-id="d1581-108">Uso da classe StringBuilder</span><span class="sxs-lookup"><span data-stu-id="d1581-108">Using the StringBuilder Class</span></span>](../../../../standard/base-types/stringbuilder.md)
- [<span data-ttu-id="d1581-109">&= Operador</span><span class="sxs-lookup"><span data-stu-id="d1581-109">&= Operator</span></span>](../../../language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="d1581-110">Cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="d1581-110">Strings</span></span>](index.md)
- [<span data-ttu-id="d1581-111">Criar novas cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="d1581-111">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="d1581-112">Manipular cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="d1581-112">Manipulating Strings</span></span>](../../../../standard/base-types/best-practices-strings.md)
