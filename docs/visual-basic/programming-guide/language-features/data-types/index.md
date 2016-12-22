---
title: "Tipos de dados no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "declarar os tipos de dados [Visual Basic]"
  - "tipificação"
  - "tipos de dados [Visual Basic]"
  - "Código do Visual Basic, tipos de dados"
  - "tipos de dados [Visual Basic], melhorando velocidade com"
ms.assetid: 5e1b9aaf-c7ca-4b29-9b22-0e82ed8e85e2
caps.latest.revision: 28
caps.handback.revision: 28
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipos de dados no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O *tipo de dados* de um elemento de programação se refere a que tipo de dados ele pode armazenar e como ele os armazena.  Tipos de dados se aplicam a todos os valores que podem ser armazenados na memória do computador ou participar da avaliação de uma expressão.  Toda variável, literal, constante, enumeração, propriedade, parâmetro de procedimento, argumento de procedimento e valor de retorno tem um tipo de dados.  
  
## Tipos de dados declarados  
 Você define um elemento de programação com uma declaração, e você deve especificar seu tipo de daos com a cláusula `As`.  A seguinte tabela mostra as declarações que você usa para declarar vários elementos.  
  
|Elemento de programação|Declaração de tipo de dados|  
|-----------------------------|---------------------------------|  
|Variável|Num [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)<br /><br /> `Dim`   `amount As Double`<br /><br /> `Static`   `yourName As String`<br /><br /> `Public`   `billsPaid As Decimal = 0`|  
|Literal|Como um caractere de tipo literal, veja "Caracteres de Tipo Literal" em [Caracteres de tipo](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).<br /><br /> `Dim searchChar As Char = "."`  `C`|  
|Constante|Num [Instrução Const](../../../../visual-basic/language-reference/statements/const-statement.md)<br /><br /> `Const`   `modulus As Single = 4.17825F`|  
|Enumeração|Num [Instrução Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)<br /><br /> `Public`   `Enum`   `colors`|  
|Propriedade|Num [Instrução Property](../../../../visual-basic/language-reference/statements/property-statement.md)<br /><br /> `Property`   `region() As String`|  
|Parâmetro de procedimento|Numa [Instrução Sub](../../../../visual-basic/language-reference/statements/sub-statement.md), [Instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md) ou [Instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md)<br /><br /> `Sub addSale(ByVal`   `amount`   `As Double)`|  
|Argumento de procedimento|No código de chamada, cada argumento é um elemento de programação que já foi declarado, ou uma expressão contendo elementos declarados.<br /><br /> `subString = Left(`  `inputString`  `,`   `5`  `)`|  
|Valor de retorno de Propriedade|Numa [Instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md)ou [Instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md)<br /><br /> `Function convert(ByVal b As Byte)`   `As String`|  
  
 Para obter uma lista de tipos de dados do Visual Basic, consulte [Tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
## Consulte também  
 [Caracteres de tipo](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)   
 [Tipos de dados elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Tipos de dados compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Tipos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Tipos de valor e referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Solucionando problemas de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Uso eficiente de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)