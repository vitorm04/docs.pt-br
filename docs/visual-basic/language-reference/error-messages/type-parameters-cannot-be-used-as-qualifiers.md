---
title: Não é possível usar parâmetros de tipo como qualificadores
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 563010efc4f3049d330ee2b38b7f59e23292e630
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595128"
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a>Não é possível usar parâmetros de tipo como qualificadores
Um elemento de programação está qualificado com uma cadeia de caracteres de qualificação que inclui um parâmetro de tipo.  
  
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
 [Referências a Elementos Declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Lista de Tipos](../../../visual-basic/language-reference/statements/type-list.md)
