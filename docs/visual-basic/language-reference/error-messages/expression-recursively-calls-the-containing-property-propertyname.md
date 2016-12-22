---
title: "A express&#227;o chama recursivamente a propriedade que cont&#233;m &#39;&lt;propertyname&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42026"
  - "BC42026"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42026"
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A express&#227;o chama recursivamente a propriedade que cont&#233;m &#39;&lt;propertyname&gt;&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma declaração no procedimento `Set` de uma definição de propriedade armazena um valor no nome da propriedade.  
  
 A abordagem recomendada para armazenar o valor de uma propriedade é definir uma variável `Private` no recipiente da propriedade e usá\-la nos procedimentos `Get` e `Set`.  O procedimento `Set` deve então armazenar o valor de entrada nesta variável `Private`.  
  
 O procedimento `Get` se comporta como um procedimento `Function`, então ele pode atribuir um valor para o nome da propriedade e retornar controle encontrando a declaração `End Get`.  A abordagem recomendada, entretanto, é incluir a variável `Private` como o valor numa declaração [Instrução Return](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 O procedimento `Set` se comporta como um procedimento `Sub`, que não retorna um valor.  Portanto, o nome do procedimento ou propriedade não tem significado especial num procedimento `Set`, e você não pode armazenar um valor nele.  
  
 O seguinte exemplo ilustra a abordagem que pode causar esse erro, seguido pela abordagem recomendada.  
  
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
  
 Por padrão, essa é uma mensagem de aviso.  Para maiores informações sobre como ocultar avisos ou tratar avisos como erros, por favor consulte [Configurando avisos no Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **Identificação do erro:**  BC42026  
  
### Para corrigir este erro  
  
-   Reescreva a definição da propriedade para usar a abordagem recomendada como ilustrada no exemplo anterior.  
  
## Consulte também  
 [Procedimentos de propriedade](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Instrução Set](../../../visual-basic/language-reference/statements/set-statement.md)