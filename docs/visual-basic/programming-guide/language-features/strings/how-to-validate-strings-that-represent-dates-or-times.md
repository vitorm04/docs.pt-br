---
title: Como validar cadeias de caracteres que representam datas ou horas
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: 5321e7a85c45ddb6ce17433bd25ce9ca2165f0a3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348408"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a>Como validar cadeias de caracteres que representam datas ou horas (Visual Basic)
O exemplo de código a seguir define um valor `Boolean` que indica se uma cadeia de caracteres representa uma data ou hora válida.  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbVbcnRegEx#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#2)]  
  
## <a name="compile-the-code"></a>Compilar o código  
 Substitua `("01/01/03")` e `"9:30 PM"` pela data e hora que você deseja validar. Você pode substituir a cadeia de caracteres por outra cadeia de caracteres embutida em código, com uma variável `String` ou por um método que retorne uma cadeia de caracteres, como `InputBox`.  
  
## <a name="robust-programming"></a>Programação Robusta  
 Use esse método para validar a cadeia de caracteres antes de tentar converter o `String` em uma variável `DateTime`. Ao marcar a data ou hora primeiro, você pode evitar a geração de uma exceção em tempo de execução.  
  
## <a name="see-also"></a>Veja também

- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [Validando cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
