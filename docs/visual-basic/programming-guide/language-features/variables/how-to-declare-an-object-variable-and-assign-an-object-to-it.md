---
title: "Como: declarar uma variável de objeto e atribuir um objeto a ela no Visual Basic | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- object variables, declaring
- declaring object variables
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
caps.latest.revision: 11
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
ms.openlocfilehash: a246df995d34308c0d5bc06aacd2a07b2e296201
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a>Como declarar uma variável de objeto e atribuir um objeto a ela no Visual Basic
Declare uma variável do [tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md) especificando `As Object` em uma [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md). Atribuir um objeto para tal variável colocando o objeto depois do sinal de igual (`=`) em uma cláusula de inicialização ou instrução de atribuição.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir declara um `Object` variável e atribui a instância atual para ele.  
  
```  
  
      Dim thisObject As Object  
thisObject = "This is an Object"  
```  
  
 Você pode combinar a declaração e atribuição Inicializando a variável como parte de sua declaração. O exemplo a seguir é equivalente ao exemplo anterior.  
  
```  
Dim thisObject As Object= "This is an Object"  
```  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Uma referência para o <xref:System>namespace.</xref:System>  
  
-   Uma classe, estrutura ou módulo no qual colocar o `Dim` instrução.  
  
-   Um procedimento no qual colocar a instrução de atribuição.  
  
## <a name="see-also"></a>Consulte também  
 [Declaração de variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Declaração de variável de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [Tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Inferência de tipo local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
