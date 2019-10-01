---
title: A expressão chama recursivamente a propriedade que contém '<propertyname>'
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: 42177f22e632e4a05b1f0b4d934f3e56ab9ff0f2
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698576"
---
# <a name="expression-recursively-calls-the-containing-property-propertyname"></a>A expressão chama recursivamente a propriedade recipiente ' \<propertyname > '
Uma instrução no procedimento `Set` de uma definição de propriedade armazena um valor no nome da propriedade.  
  
 A abordagem recomendada para manter o valor de uma propriedade é definir uma variável `Private` no contêiner da propriedade e usá-la nos procedimentos `Get` e `Set`. O procedimento `Set` deve armazenar o valor de entrada nessa variável `Private`.  
  
 O procedimento `Get` se comporta como um procedimento `Function`, portanto, ele pode atribuir um valor ao nome da propriedade e ao controle de retorno ao encontrar a instrução `End Get`. No entanto, a abordagem recomendada é incluir a variável `Private` como o valor em uma [instrução return](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 O procedimento `Set` se comporta como um procedimento `Sub`, que não retorna um valor. Portanto, o nome do procedimento ou da propriedade não tem um significado especial dentro de um procedimento `Set` e você não pode armazenar um valor nele.  
  
 O exemplo a seguir ilustra a abordagem que pode causar esse erro, seguida da abordagem recomendada.  
  
```vb  
Public Class illustrateProperties  
' The code in the following property causes this error.  
    Public Property badProp() As Char  
        Get  
            Dim charValue As Char  
            ' Insert code to update charValue.  
            badProp = charValue  
        End Get  
        Set(ByVal Value As Char)  
            ' The following statement causes this error.  
            badProp = Value  
            ' The value stored in the local variable badProp  
            ' is not used by the Get procedure in this property.  
        End Set  
    End Property  
' The following code uses the recommended approach.  
    Private propValue As Char  
    Public Property goodProp() As Char  
        Get  
            ' Insert code to update propValue.  
            Return propValue  
        End Get  
        Set(ByVal Value As Char)  
            propValue = Value  
        End Set  
    End Property  
End Class  
```  
  
 Por padrão, esta mensagem é um aviso. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC42026  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Reescreva a definição de propriedade para usar a abordagem recomendada, conforme ilustrado no exemplo anterior.  
  
## <a name="see-also"></a>Consulte também

- [Procedimentos de Propriedade](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Instrução Set](../../../visual-basic/language-reference/statements/set-statement.md)
