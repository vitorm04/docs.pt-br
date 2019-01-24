---
title: 'Como: Validar cadeias de caracteres que representam datas ou horas (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: 1a838d9d156ad9c05a70a4d4d72db1a288731c9b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685393"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a>Como: Validar cadeias de caracteres que representam datas ou horas (Visual Basic)
O seguinte exemplo de código define uma `Boolean` valor que indica se uma cadeia de caracteres representa uma data ou hora válida.  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbVbcnRegEx#2](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-strings-that-represent-dates-or-times_1.vb)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Substitua `("01/01/03")` e `"9:30 PM"` com a data e hora que você deseja validar. Você pode substituir a cadeia de caracteres com outra cadeia de caracteres embutidos, com um `String` variável, ou com um método que retorna uma cadeia de caracteres, como `InputBox`.  
  
## <a name="robust-programming"></a>Programação robusta  
 Use esse método para validar a cadeia de caracteres antes de tentar converter o `String` para um `DateTime` variável. Verificando a data ou hora pela primeira vez, você pode evitar gerar uma exceção em tempo de execução.  
  
## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [Validando cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
