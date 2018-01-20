---
title: Como criar cadeias de caracteres usando StringBuilder no Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9def5da754d9075a8b498ac80e624caae5c97b96
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="07df6-102">Como criar cadeias de caracteres usando StringBuilder no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="07df6-102">How to: Create Strings Using a StringBuilder in Visual Basic</span></span>
<span data-ttu-id="07df6-103">Esse exemplo constrói uma cadeia de caracteres longa de várias cadeias menores utilizando o <xref:System.Text.StringBuilder> classe.</span><span class="sxs-lookup"><span data-stu-id="07df6-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="07df6-104">O <xref:System.Text.StringBuilder> classe é mais eficiente do que o `&=` operador para concatenar várias cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="07df6-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07df6-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="07df6-105">Example</span></span>  
 <span data-ttu-id="07df6-106">O exemplo a seguir cria uma instância do <xref:System.Text.StringBuilder> classe, anexa 1.000 cadeias de caracteres a essa instância e, em seguida, retorna sua representação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="07df6-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation.</span></span>  
  
 [!code-vb[VbVbalrStrings#70](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-strings-using-a-stringbuilder_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="07df6-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07df6-107">See Also</span></span>  
 [<span data-ttu-id="07df6-108">Uso da classe StringBuilder</span><span class="sxs-lookup"><span data-stu-id="07df6-108">Using the StringBuilder Class</span></span>](../../../../standard/base-types/stringbuilder.md)  
 [<span data-ttu-id="07df6-109">Operador &=</span><span class="sxs-lookup"><span data-stu-id="07df6-109">&= Operator</span></span>](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [<span data-ttu-id="07df6-110">Cadeias de Caracteres</span><span class="sxs-lookup"><span data-stu-id="07df6-110">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)  
 [<span data-ttu-id="07df6-111">Criando novas cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="07df6-111">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)  
 [<span data-ttu-id="07df6-112">Manipulando cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="07df6-112">Manipulating Strings</span></span>](../../../../standard/base-types/manipulating-strings.md)  
 [<span data-ttu-id="07df6-113">Exemplo de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="07df6-113">Strings Sample</span></span>](http://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02)
