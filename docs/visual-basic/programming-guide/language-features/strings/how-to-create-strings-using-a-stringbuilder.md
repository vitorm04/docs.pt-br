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
ms.openlocfilehash: c799794b319843b0239ce9589e0c556c603c8617
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a>Como criar cadeias de caracteres usando StringBuilder no Visual Basic
Esse exemplo constrói uma cadeia de caracteres longa de várias cadeias menores utilizando o <xref:System.Text.StringBuilder> classe. O <xref:System.Text.StringBuilder> classe é mais eficiente do que o `&=` operador para concatenar várias cadeias de caracteres.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma instância do <xref:System.Text.StringBuilder> classe, anexa 1.000 cadeias de caracteres a essa instância e, em seguida, retorna sua representação de cadeia de caracteres.  
  
 [!code-vb[VbVbalrStrings#70](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-strings-using-a-stringbuilder_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Uso da classe StringBuilder](../../../../standard/base-types/stringbuilder.md)  
 [Operador &=](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [Cadeias de Caracteres](../../../../visual-basic/programming-guide/language-features/strings/index.md)  
 [Criando novas cadeias de caracteres](../../../../standard/base-types/creating-new.md)  
 [Manipulando cadeias de caracteres](../../../../standard/base-types/manipulating-strings.md)  
 [Exemplo de cadeias de caracteres](http://msdn.microsoft.com/en-us/be9e82a3-dc95-4aaa-9396-61b66e467e02)
