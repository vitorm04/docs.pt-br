---
title: 'Como: Validar cadeias de caracteres que representam datas ou horas (Visual Basic) | Documentos do Microsoft'
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
- strings [Visual Basic], validating
- String data type, validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
caps.latest.revision: 11
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
ms.openlocfilehash: aec2c21fa6088ce70b6e0b221b194f22e3d599a7
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a><span data-ttu-id="0d37f-102">Como validar cadeias de caracteres que representam datas ou horas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d37f-102">How to: Validate Strings That Represent Dates or Times (Visual Basic)</span></span>
<span data-ttu-id="0d37f-103">O seguinte exemplo de código define uma `Boolean` valor que indica se uma cadeia de caracteres representa uma data ou hora válida.</span><span class="sxs-lookup"><span data-stu-id="0d37f-103">The following code example sets a `Boolean` value that indicates whether a string represents a valid date or time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d37f-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0d37f-104">Example</span></span>  
 <span data-ttu-id="0d37f-105">[!code-vb[VbVbcnRegEx n º&2;](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-strings-that-represent-dates-or-times_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="0d37f-105">[!code-vb[VbVbcnRegEx#2](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-strings-that-represent-dates-or-times_1.vb)]</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0d37f-106">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="0d37f-106">Compiling the Code</span></span>  
 <span data-ttu-id="0d37f-107">Substitua `("01/01/03")` e `"9:30 PM"` com a data e hora que você deseja validar.</span><span class="sxs-lookup"><span data-stu-id="0d37f-107">Replace `("01/01/03")` and `"9:30 PM"` with the date and time you want to validate.</span></span> <span data-ttu-id="0d37f-108">Você pode substituir a cadeia de caracteres com outra cadeia de caracteres embutida, com um `String` variável, ou com um método que retorna uma cadeia de caracteres, como `InputBox`.</span><span class="sxs-lookup"><span data-stu-id="0d37f-108">You can replace the string with another hard-coded string, with a `String` variable, or with a method that returns a string, such as `InputBox`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="0d37f-109">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="0d37f-109">Robust Programming</span></span>  
 <span data-ttu-id="0d37f-110">Use esse método para validar a cadeia de caracteres antes de tentar converter o `String` para um `DateTime` variável.</span><span class="sxs-lookup"><span data-stu-id="0d37f-110">Use this method to validate the string before trying to convert the `String` to a `DateTime` variable.</span></span> <span data-ttu-id="0d37f-111">Verificando a data ou hora primeiro, você pode evitar gerar uma exceção em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0d37f-111">By checking the date or time first, you can avoid generating an exception at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d37f-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d37f-112">See Also</span></span>  
 <span data-ttu-id="0d37f-113"><xref:Microsoft.VisualBasic.Information.IsDate%2A></xref:Microsoft.VisualBasic.Information.IsDate%2A></span><span class="sxs-lookup"><span data-stu-id="0d37f-113"><xref:Microsoft.VisualBasic.Information.IsDate%2A></span></span>   
 <span data-ttu-id="0d37f-114"><xref:Microsoft.VisualBasic.Interaction.InputBox%2A></xref:Microsoft.VisualBasic.Interaction.InputBox%2A></span><span class="sxs-lookup"><span data-stu-id="0d37f-114"><xref:Microsoft.VisualBasic.Interaction.InputBox%2A></span></span>   
<span data-ttu-id="0d37f-115"> [Validando cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)</span><span class="sxs-lookup"><span data-stu-id="0d37f-115"> [Validating Strings in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)</span></span>
