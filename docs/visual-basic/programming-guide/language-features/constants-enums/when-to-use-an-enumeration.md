---
title: "Quando usar uma enumera&#231;&#227;o (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "enumerações [Visual Basic]"
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Quando usar uma enumera&#231;&#227;o (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Enumerações oferecem uma maneira fácil para trabalhar com conjuntos de constantes relacionadas.  Uma enumeração, ou `Enum`, é um nome simbólico para um conjunto de valores.  Enumerações são tratadas como tipo de dados, e você pode usá\-las para criar conjuntos de constantes para uso com variáveis e propriedades.  
  
## Quando usar uma enumeração  
 Sempre que um procedimento aceita um conjunto limitado de variáveis, considere o uso de uma enumeração.  Enumerações criam código mais claro e legível, especialmente quando são usados nomes significativos.  
  
 Os benefícios de usar enumerações incluem:  
  
-   Reduz erros causados pela transpô ou números de erros de digitação.  
  
-   Torna fácil alterar os valores no futuro.  
  
-   Torna o código mais fácil de ler, o que significa que é menos provável a ocorrência de erros.  
  
-   Garante compatibilidade futura.  Com enumerações, seu código é menos provável que falham se no futuro alguém altera os valores correspondentes aos nomes de membro.  
  
## Enumerações de nomeação.  
 Use uma convenção de nomenclatura para membros de enumeração.  Quando [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] encontrar um nome de membro de enumeração, uma exceção pode ser lançada se outras bibliotecas de tipos referenciada contiverem o mesmo nome.  Use um prefixo exclusivo que identifica os valores de seu aplicativo ou componente.  
  
 Quando nos referimos a um membro de uma enumeração, você deve qualificar o nome do membro com o nome da enumeração ou então usar o `Imports` instrução.  Para obter mais informações, consulte [Enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
## Enumerações predefinidas  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]oferece um número de enumerações predefinidos, como `FirstDayOfWeek` e `MsgBoxResul`t, para facilitar o seu código.  Para obter uma lista desses consulte [Constantes e enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md).  
  
## Consulte também  
 [Como declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [Como fazer referência a um membro de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)   
 [Enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [Como iterar em uma enumeração no Visual Basic](../Topic/How%20to:%20Iterate%20Through%20An%20Enumeration%20in%20Visual%20Basic.md)   
 [Como determinar a cadeia de caracteres associada a um valor de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)   
 [Instrução Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)   
 [Constantes e enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md)