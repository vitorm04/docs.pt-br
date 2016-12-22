---
title: "Determinando o tipo de objeto (Visual Basic) | Microsoft Docs"
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
  - "classes [Visual Basic], descobrindo a que um objeto pertence"
  - "variáveis de objeto, testando valores"
  - "objetos [Visual Basic], determinação do tipo"
  - "Função TypeName"
  - "expressão TypeOf...Is, tipo de objeto em tempo de execução"
  - "tipos [Visual Basic], determinando os tipos de objeto do Visual Basic"
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Determinando o tipo de objeto (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Variáveis de objeto genérico \(ou seja, variáveis que você declara como `Object`\) pode conter objetos de qualquer classe.  Ao usar variáveis do tipo `Object`, talvez você precise tomar ações diferentes, com base na classe do objeto; Por exemplo, alguns objetos podem não suportar uma determinada propriedade ou método.  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]fornece dois meios de determinar qual tipo de objeto é armazenado em uma variável de objeto: o `TypeName` função e o `TypeOf...Is` operador.  
  
## TypeName e TypeOf…É  
 O `TypeName` função retorna uma seqüência de caracteres e é a melhor opção quando você precisar armazenar ou exibir o nome da classe de um objeto, conforme mostrado no fragmento de código a seguir:  
  
 [!code-vb[VbVbalrOOP#92](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_1.vb)]  
  
 O `TypeOf...Is` operador é a melhor opção para testar o tipo de um objeto, porque é muito mais rápido que uma comparação de seqüência equivalente usando `TypeName`.  O fragmento de código a seguir usa `TypeOf...Is` dentro de um `If...Then...Else` instrução:  
  
 [!code-vb[VbVbalrOOP#93](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_2.vb)]  
  
 Um conselho é vencimento aqui.  O `TypeOf...Is` o operador retorna `True` se um objeto for de um tipo específico, ou é derivado de um tipo específico.  Quase tudo o que você pode fazer com [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] envolve a objetos, que incluem alguns elementos não é normalmente considerado como objetos, como, por exemplo, seqüências de caracteres e inteiros.  Esses objetos são obtidos e herdam os métodos de <xref:System.Object>.  Quando passado um `Integer` e avaliado com `Object`, o `TypeOf...Is` o operador retorna `True`.  O exemplo a seguir informa que o parâmetro `InParam` é um `Object` e um `Integer`:  
  
 [!code-vb[VbVbalrOOP#94](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_3.vb)]  
  
 O exemplo a seguir usa ambos `TypeOf...Is` e `TypeName` para determinar o tipo de objeto passado para ele no `Ctrl` argumento.  O `TestObject` chamadas de procedimento `ShowType` com três tipos diferentes de controles.  
  
#### Para executar o exemplo.  
  
1.  Crie um novo projeto Windows Application e adicione um <xref:System.Windows.Forms.Button> controle, uma <xref:System.Windows.Forms.CheckBox> controle e um <xref:System.Windows.Forms.RadioButton> o controle ao formulário.  
  
2.  Com o botão no formulário, ligue para o `TestObject` procedimento.  
  
3.  Adicione o seguinte código ao seu formulário:  
  
     [!code-vb[VbVbalrOOP#95](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_4.vb)]  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.Information.TypeName%2A>   
 [Chamando uma propriedade ou um método usando o nome de uma cadeia de caracteres](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)   
 [Tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [Instrução If...Then...Else](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)   
 [Tipo de dados da cadeia de caracteres](../../../../visual-basic/language-reference/data-types/string-data-type.md)   
 [Tipo de dados inteiro](../../../../visual-basic/language-reference/data-types/integer-data-type.md)