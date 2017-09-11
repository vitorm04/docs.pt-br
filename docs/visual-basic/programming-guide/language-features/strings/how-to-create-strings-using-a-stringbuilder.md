---
title: 'Como: criar cadeias de caracteres usando StringBuilder no Visual Basic | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 1b78138346b32a16bca6bd731c6b494e08531d6c
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="f4016-102">Como criar cadeias de caracteres usando StringBuilder no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f4016-102">How to: Create Strings Using a StringBuilder in Visual Basic</span></span>
<span data-ttu-id="f4016-103">Este exemplo constrói uma cadeia de caracteres longa de várias cadeias menores utilizando a <xref:System.Text.StringBuilder>classe.</xref:System.Text.StringBuilder></span><span class="sxs-lookup"><span data-stu-id="f4016-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="f4016-104">O <xref:System.Text.StringBuilder>classe é mais eficiente do que o `&=` operador para concatenar várias cadeias.</xref:System.Text.StringBuilder></span><span class="sxs-lookup"><span data-stu-id="f4016-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4016-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f4016-105">Example</span></span>  
 <span data-ttu-id="f4016-106">O exemplo a seguir cria uma instância da <xref:System.Text.StringBuilder>classe, anexa 1.000 cadeias de caracteres a essa instância e, em seguida, retorna a representação da cadeia de caracteres.</xref:System.Text.StringBuilder></span><span class="sxs-lookup"><span data-stu-id="f4016-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation.</span></span>  
  
 <span data-ttu-id="f4016-107">[!code-vb[VbVbalrStrings&#70;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-strings-using-a-stringbuilder_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f4016-107">[!code-vb[VbVbalrStrings#70](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-strings-using-a-stringbuilder_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4016-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f4016-108">See Also</span></span>  
 <span data-ttu-id="f4016-109">[Usando a classe StringBuilder](http://msdn.microsoft.com/library/5c14867c-9a99-45bc-ae7f-2686700d377a) </span><span class="sxs-lookup"><span data-stu-id="f4016-109">[Using the StringBuilder Class](http://msdn.microsoft.com/library/5c14867c-9a99-45bc-ae7f-2686700d377a) </span></span>  
<span data-ttu-id="f4016-110"> [< / Operador =](../../../../visual-basic/language-reference/operators/and-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="f4016-110"> [&= Operator](../../../../visual-basic/language-reference/operators/and-assignment-operator.md) </span></span>  
<span data-ttu-id="f4016-111"> [Cadeias de caracteres](../../../../visual-basic/programming-guide/language-features/strings/index.md) </span><span class="sxs-lookup"><span data-stu-id="f4016-111"> [Strings](../../../../visual-basic/programming-guide/language-features/strings/index.md) </span></span>  
<span data-ttu-id="f4016-112"> [Criando novas cadeias de caracteres](http://msdn.microsoft.com/library/06fdf123-2fac-4459-8904-eb48ab908a30) </span><span class="sxs-lookup"><span data-stu-id="f4016-112"> [Creating New Strings](http://msdn.microsoft.com/library/06fdf123-2fac-4459-8904-eb48ab908a30) </span></span>  
<span data-ttu-id="f4016-113"> [Manipulando cadeias de caracteres](http://msdn.microsoft.com/library/d4568ff3-9f83-4549-acd8-47aec2194ac0) </span><span class="sxs-lookup"><span data-stu-id="f4016-113"> [Manipulating Strings](http://msdn.microsoft.com/library/d4568ff3-9f83-4549-acd8-47aec2194ac0) </span></span>  
<span data-ttu-id="f4016-114"> [Exemplo de cadeias de caracteres](http://msdn.microsoft.com/en-us/be9e82a3-dc95-4aaa-9396-61b66e467e02)</span><span class="sxs-lookup"><span data-stu-id="f4016-114"> [Strings Sample](http://msdn.microsoft.com/en-us/be9e82a3-dc95-4aaa-9396-61b66e467e02)</span></span>
