---
title: A expressão chama recursivamente a propriedade recipiente &#39; &lt;propertyname&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: f14e2645772b22a8f6ff2385dcd316a42d1d5cf0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588837"
---
# <a name="expression-recursively-calls-the-containing-property-39ltpropertynamegt39"></a>A expressão chama recursivamente a propriedade recipiente &#39; &lt;propertyname&gt;&#39;
Uma instrução no `Set` procedimento com uma definição de propriedade armazena um valor para o nome da propriedade.  
  
 A abordagem recomendada para armazenar o valor de uma propriedade é definir uma `Private` variável no recipiente da propriedade e usá-lo em ambos os `Get` e `Set` procedimentos. O `Set` procedimento deve, em seguida, armazenar o valor de entrada neste `Private` variável.  
  
 O `Get` procedimento se comporta como uma `Function` procedimento, para que possa atribuir um valor para o nome da propriedade e retornar controle encontrando o `End Get` instrução. No entanto, é a abordagem recomendada, inclua o `Private` variável como o valor em uma [instrução Return](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 O `Set` procedimento se comporta como uma `Sub` procedimento, que não retorna um valor. Portanto, o nome do procedimento ou propriedade não tem significado especial em um `Set` procedimento e você não pode armazenar um valor nele.  
  
 O exemplo a seguir ilustra a abordagem que pode causar esse erro, seguido pela abordagem recomendada.  
  
```  
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
  
-   Reescreva a definição de propriedade para usar a abordagem recomendada, conforme ilustrado no exemplo anterior.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos de Propriedade](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Instrução Set](../../../visual-basic/language-reference/statements/set-statement.md)
