---
title: Como validar cadeias de caracteres que representam datas ou horas
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: f3654894e274404410179dab04422e20f6040440
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072594"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a><span data-ttu-id="9fb99-102">Como validar cadeias de caracteres que representam datas ou horas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9fb99-102">How to: Validate Strings That Represent Dates or Times (Visual Basic)</span></span>

<span data-ttu-id="9fb99-103">O exemplo de código a seguir define um `Boolean` valor que indica se uma cadeia de caracteres representa uma data ou hora válida.</span><span class="sxs-lookup"><span data-stu-id="9fb99-103">The following code example sets a `Boolean` value that indicates whether a string represents a valid date or time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fb99-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9fb99-104">Example</span></span>  

 [!code-vb[VbVbcnRegEx#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#2)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="9fb99-105">Compilar o código</span><span class="sxs-lookup"><span data-stu-id="9fb99-105">Compile the code</span></span>  

 <span data-ttu-id="9fb99-106">Substitua `("01/01/03")` e `"9:30 PM"` pela data e hora que você deseja validar.</span><span class="sxs-lookup"><span data-stu-id="9fb99-106">Replace `("01/01/03")` and `"9:30 PM"` with the date and time you want to validate.</span></span> <span data-ttu-id="9fb99-107">Você pode substituir a cadeia de caracteres por outra cadeia de caracteres embutida em código, com uma `String` variável ou por um método que retorne uma cadeia de caracteres, como `InputBox` .</span><span class="sxs-lookup"><span data-stu-id="9fb99-107">You can replace the string with another hard-coded string, with a `String` variable, or with a method that returns a string, such as `InputBox`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="9fb99-108">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="9fb99-108">Robust Programming</span></span>  

 <span data-ttu-id="9fb99-109">Use este método para validar a cadeia de caracteres antes de tentar converter o `String` em uma `DateTime` variável.</span><span class="sxs-lookup"><span data-stu-id="9fb99-109">Use this method to validate the string before trying to convert the `String` to a `DateTime` variable.</span></span> <span data-ttu-id="9fb99-110">Ao marcar a data ou hora primeiro, você pode evitar a geração de uma exceção em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9fb99-110">By checking the date or time first, you can avoid generating an exception at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fb99-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="9fb99-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [<span data-ttu-id="9fb99-112">Validando cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9fb99-112">Validating Strings in Visual Basic</span></span>](validating-strings.md)
