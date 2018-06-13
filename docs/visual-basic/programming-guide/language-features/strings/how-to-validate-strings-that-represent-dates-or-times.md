---
title: Como validar cadeias de caracteres que representam datas ou horas (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: 411c8517783421b2472c3e4aa77287f8252f179b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647856"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a>Como validar cadeias de caracteres que representam datas ou horas (Visual Basic)
O seguinte exemplo de código define uma `Boolean` valor que indica se uma cadeia de caracteres representa uma data ou hora válida.  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbVbcnRegEx#2](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-strings-that-represent-dates-or-times_1.vb)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Substituir `("01/01/03")` e `"9:30 PM"` com a data e hora que você deseja validar. Você pode substituir a cadeia de caracteres com outra cadeia embutidos, com um `String` variável, ou com um método que retorna uma cadeia de caracteres, como `InputBox`.  
  
## <a name="robust-programming"></a>Programação robusta  
 Use esse método para validar a cadeia de caracteres antes de tentar converter o `String` para um `DateTime` variável. Verificando a data ou hora primeiro, você pode evitar gerar uma exceção em tempo de execução.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Information.IsDate%2A>  
 <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>  
 [Validando cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
