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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: bf3f5136a532c2b12e11c5cbe92cc004fb3910c2
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a>Como validar cadeias de caracteres que representam datas ou horas (Visual Basic)
O seguinte exemplo de código define uma `Boolean` valor que indica se uma cadeia de caracteres representa uma data ou hora válida.  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbVbcnRegEx n º&2;](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-strings-that-represent-dates-or-times_1.vb)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Substitua `("01/01/03")` e `"9:30 PM"` com a data e hora que você deseja validar. Você pode substituir a cadeia de caracteres com outra cadeia de caracteres embutida, com um `String` variável, ou com um método que retorna uma cadeia de caracteres, como `InputBox`.  
  
## <a name="robust-programming"></a>Programação robusta  
 Use esse método para validar a cadeia de caracteres antes de tentar converter o `String` para um `DateTime` variável. Verificando a data ou hora primeiro, você pode evitar gerar uma exceção em tempo de execução.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Information.IsDate%2A></xref:Microsoft.VisualBasic.Information.IsDate%2A>   
 <xref:Microsoft.VisualBasic.Interaction.InputBox%2A></xref:Microsoft.VisualBasic.Interaction.InputBox%2A>   
 [Validando cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
