---
title: Não é possível usar parâmetros de tipo como qualificadores
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 88b5f365c47b98964d9f5a0d22a941d85dcfb95f
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592143"
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a>Não é possível usar parâmetros de tipo como qualificadores
Um elemento de programação é qualificado com uma cadeia de caracteres de qualificação que inclui um parâmetro de tipo.  
  
 Um parâmetro de tipo representa um requisito para um tipo que deve ser fornecido quando o tipo genérico é construído. Ele não representa um tipo definido específico. Uma cadeia de caracteres de qualificação deve incluir apenas elementos que são definidos no momento da compilação.  
  
 As instruções a seguir podem gerar esse erro.  
  
```vb  
Public Function checkText(Of c As System.Windows.Forms.Control)(  
    ByVal badText As String) As Boolean  
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.  
End Function  
```  
  
 **ID do erro:** BC32098  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Remova o parâmetro de tipo da cadeia de caracteres de qualificação ou substitua-o por um tipo definido.  
  
2. Se você precisar usar um tipo construído para localizar o elemento de programação que está sendo qualificado, deverá usar a lógica de programa adicional.  
  
## <a name="see-also"></a>Consulte também

- [Referências a Elementos Declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Lista de Tipos](../../../visual-basic/language-reference/statements/type-list.md)
