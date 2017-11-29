---
title: Como validar cadeias de caracteres que representam datas ou horas (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ed3201ef2bbef97eebbafa5ef128ca015adac013
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a><span data-ttu-id="fcd99-102">Como validar cadeias de caracteres que representam datas ou horas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fcd99-102">How to: Validate Strings That Represent Dates or Times (Visual Basic)</span></span>
<span data-ttu-id="fcd99-103">O seguinte exemplo de código define uma `Boolean` valor que indica se uma cadeia de caracteres representa uma data ou hora válida.</span><span class="sxs-lookup"><span data-stu-id="fcd99-103">The following code example sets a `Boolean` value that indicates whether a string represents a valid date or time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fcd99-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fcd99-104">Example</span></span>  
 [!code-vb[VbVbcnRegEx#2](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-strings-that-represent-dates-or-times_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fcd99-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="fcd99-105">Compiling the Code</span></span>  
 <span data-ttu-id="fcd99-106">Substituir `("01/01/03")` e `"9:30 PM"` com a data e hora que você deseja validar.</span><span class="sxs-lookup"><span data-stu-id="fcd99-106">Replace `("01/01/03")` and `"9:30 PM"` with the date and time you want to validate.</span></span> <span data-ttu-id="fcd99-107">Você pode substituir a cadeia de caracteres com outra cadeia embutidos, com um `String` variável, ou com um método que retorna uma cadeia de caracteres, como `InputBox`.</span><span class="sxs-lookup"><span data-stu-id="fcd99-107">You can replace the string with another hard-coded string, with a `String` variable, or with a method that returns a string, such as `InputBox`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="fcd99-108">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="fcd99-108">Robust Programming</span></span>  
 <span data-ttu-id="fcd99-109">Use esse método para validar a cadeia de caracteres antes de tentar converter o `String` para um `DateTime` variável.</span><span class="sxs-lookup"><span data-stu-id="fcd99-109">Use this method to validate the string before trying to convert the `String` to a `DateTime` variable.</span></span> <span data-ttu-id="fcd99-110">Verificando a data ou hora primeiro, você pode evitar gerar uma exceção em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="fcd99-110">By checking the date or time first, you can avoid generating an exception at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcd99-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fcd99-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Information.IsDate%2A>  
 <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>  
 [<span data-ttu-id="fcd99-112">Validando cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fcd99-112">Validating Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
