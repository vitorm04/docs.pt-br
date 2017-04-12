---
title: "Parâmetros de tipo não podem ser usados como qualificadores | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32098
- bc32098
dev_langs:
- VB
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
caps.latest.revision: 9
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
ms.openlocfilehash: 1931945b1ae58019096a7ed1a27d2aeda76f4e45
ms.lasthandoff: 03/13/2017

---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a>Não é possível usar parâmetros de tipo como qualificadores
Um elemento de programação é qualificado com uma cadeia de caracteres de qualificação que inclui um parâmetro de tipo.  
  
 Um parâmetro de tipo representa um requisito para um tipo que deve ser fornecido quando o tipo genérico é construído. Ele não representa um tipo específico de definidos. Uma cadeia de caracteres de qualificação deve incluir somente os elementos que são definidos em tempo de compilação.  
  
 As instruções a seguir podem gerar esse erro.  
  
```  
Public Function checkText(Of c As System.Windows.Forms.Control)(  
    ByVal badText As String) As Boolean  
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.  
End Function  
```  
  
 **ID do erro:** BC32098  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Remova o parâmetro de tipo de cadeia de caracteres de qualificação ou substituí-lo com um tipo definido.  
  
2.  Se você precisar usar um tipo construído para localizar o elemento de programação que está sendo qualificado, você deve usar lógica adicional do programa.  
  
## <a name="see-also"></a>Consulte também  
 [Referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Lista de Tipos](../../../visual-basic/language-reference/statements/type-list.md)
