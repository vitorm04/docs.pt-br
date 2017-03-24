---
title: "A expressão chama recursivamente a propriedade recipiente &quot;&lt;propertyname&gt;&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42026
- BC42026
dev_langs:
- VB
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
caps.latest.revision: 10
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
ms.openlocfilehash: ca20bf1a539f2727a80f8e781c1e9ebc5a4a253d
ms.lasthandoff: 03/13/2017

---
# <a name="expression-recursively-calls-the-containing-property-39ltpropertynamegt39"></a>A expressão chama recursivamente a propriedade recipiente '&lt;propertyname&gt;'
Uma instrução no `Set` procedimento de uma definição de propriedade armazena um valor no nome da propriedade.  
  
 A abordagem recomendada para armazenar o valor de uma propriedade é definir uma `Private` variável no recipiente da propriedade e usá-lo em ambos os `Get` e `Set` procedimentos. O `Set` procedimento deve então armazenar o valor de entrada nesta `Private` variável.  
  
 O `Get` procedimento se comporta como um `Function` procedimento, para que possa atribuir um valor ao nome da propriedade e retornar controle encontrando o `End Get` instrução. A abordagem recomendada, entretanto, é incluir a `Private` variável como o valor em uma [instrução Return](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 O `Set` procedimento se comporta como uma `Sub` procedimento, que não retorna um valor. Portanto, o nome do procedimento ou propriedade não tem significado especial em uma `Set` procedimento e você não pode armazenar um valor nele.  
  
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
  
 Por padrão, esta mensagem é um aviso. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC42026  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Reescreva a definição de propriedade para usar a abordagem recomendada, conforme ilustrado no exemplo anterior.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos de propriedade](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Instrução Set](../../../visual-basic/language-reference/statements/set-statement.md)
