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
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: ad1369079e1c08e01d0d15933a53ecc84c975d61
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a>Como criar cadeias de caracteres usando StringBuilder no Visual Basic
Este exemplo constrói uma cadeia de caracteres longa de várias cadeias menores utilizando a <xref:System.Text.StringBuilder>classe.</xref:System.Text.StringBuilder> O <xref:System.Text.StringBuilder>classe é mais eficiente do que o `&=` operador para concatenar várias cadeias.</xref:System.Text.StringBuilder>  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma instância da <xref:System.Text.StringBuilder>classe, anexa 1.000 cadeias de caracteres a essa instância e, em seguida, retorna a representação da cadeia de caracteres.</xref:System.Text.StringBuilder>  
  
 [!code-vb[VbVbalrStrings&#70;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-strings-using-a-stringbuilder_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Usando a classe StringBuilder](http://msdn.microsoft.com/library/5c14867c-9a99-45bc-ae7f-2686700d377a)   
 [< / Operador =](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)   
 [Cadeias de caracteres](../../../../visual-basic/programming-guide/language-features/strings/index.md)   
 [Criando novas cadeias de caracteres](http://msdn.microsoft.com/library/06fdf123-2fac-4459-8904-eb48ab908a30)   
 [Manipulando cadeias de caracteres](http://msdn.microsoft.com/library/d4568ff3-9f83-4549-acd8-47aec2194ac0)   
 [Exemplo de cadeias de caracteres](http://msdn.microsoft.com/en-us/be9e82a3-dc95-4aaa-9396-61b66e467e02)
