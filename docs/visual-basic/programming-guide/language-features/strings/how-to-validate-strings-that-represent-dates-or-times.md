---
title: 'Como: Validar cadeias de caracteres que representam datas ou horas (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: f24ff05e48327c21c02eb92b07db17266f743a80
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024606"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a><span data-ttu-id="b3daf-102">Como: Validar cadeias de caracteres que representam datas ou horas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3daf-102">How to: Validate Strings That Represent Dates or Times (Visual Basic)</span></span>
<span data-ttu-id="b3daf-103">O seguinte exemplo de código define uma `Boolean` valor que indica se uma cadeia de caracteres representa uma data ou hora válida.</span><span class="sxs-lookup"><span data-stu-id="b3daf-103">The following code example sets a `Boolean` value that indicates whether a string represents a valid date or time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3daf-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b3daf-104">Example</span></span>  
 [!code-vb[VbVbcnRegEx#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b3daf-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="b3daf-105">Compiling the Code</span></span>  
 <span data-ttu-id="b3daf-106">Substitua `("01/01/03")` e `"9:30 PM"` com a data e hora que você deseja validar.</span><span class="sxs-lookup"><span data-stu-id="b3daf-106">Replace `("01/01/03")` and `"9:30 PM"` with the date and time you want to validate.</span></span> <span data-ttu-id="b3daf-107">Você pode substituir a cadeia de caracteres com outra cadeia de caracteres embutidos, com um `String` variável, ou com um método que retorna uma cadeia de caracteres, como `InputBox`.</span><span class="sxs-lookup"><span data-stu-id="b3daf-107">You can replace the string with another hard-coded string, with a `String` variable, or with a method that returns a string, such as `InputBox`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b3daf-108">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="b3daf-108">Robust Programming</span></span>  
 <span data-ttu-id="b3daf-109">Use esse método para validar a cadeia de caracteres antes de tentar converter o `String` para um `DateTime` variável.</span><span class="sxs-lookup"><span data-stu-id="b3daf-109">Use this method to validate the string before trying to convert the `String` to a `DateTime` variable.</span></span> <span data-ttu-id="b3daf-110">Verificando a data ou hora pela primeira vez, você pode evitar gerar uma exceção em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b3daf-110">By checking the date or time first, you can avoid generating an exception at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3daf-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3daf-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [<span data-ttu-id="b3daf-112">Validando cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b3daf-112">Validating Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
