---
title: 'Como: Declare uma variável de objeto e atribuir um objeto a ela no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: fb6411efc190dce335422369a8d2bbff564b9523
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938210"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a>Como: Declare uma variável de objeto e atribuir um objeto a ela no Visual Basic
Declare uma variável do [tipo de dados do objeto](../../../../visual-basic/language-reference/data-types/object-data-type.md) especificando `As Object` em uma [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md). Atribuir um objeto para tal variável colocando o objeto após o sinal de igual (`=`) em uma cláusula de inicialização ou instrução de atribuição.  
  
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
  
- Uma referência para o <xref:System> namespace.  
  
- Uma classe, estrutura ou módulo no qual colocar o `Dim` instrução.  
  
- Um procedimento no qual colocar a instrução de atribuição.  
  
## <a name="see-also"></a>Consulte também

- [Declaração de Variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Variáveis de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Declaração de Variável do Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Tipo de Dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Inferência de Tipo de Variável Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
