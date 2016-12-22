---
title: "Valores de vari&#225;vel de objeto (Visual Basic) | Microsoft Docs"
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
  - "tipos de dados [Visual Basic], variável de objeto"
  - "variáveis de objeto, Valores"
  - "Valores, variáveis de objeto of"
  - "variáveis [Visual Basic], Objeto "
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Valores de vari&#225;vel de objeto (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Uma variável do [Tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md) pode referir\-se a dados de qualquer tipo.  O valor que armazenamos em uma variável `Object` é mantido em outro lugar na memória, enquanto a variável contém um ponteiro para os dados.  
  
## Funções Classificadoras de Objeto  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fornece funções que retornam informações sobre o que uma variável `Object` refere\-se a, conforme mostrado na tabela a seguir.  
  
|Função|Retorna True se o objeto variável se refere a|  
|------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|Uma matriz de valores, em vez um valor único|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|Um valor [Tipo de dados Data](../../../../visual-basic/language-reference/data-types/date-data-type.md), ou uma sequência de caracteres que pode ser interpretada como uma data e valor de tempo|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|Um objeto do tipo <xref:System.DBNull>, que representa dados ausentes ou inexistentes|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|Um objeto de exceção, que é derivado de <xref:System.Exception>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|[nada](../../../../visual-basic/language-reference/nothing.md), ou seja, nenhum objeto atualmente atribuído à variável|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|Um número ou uma sequência de caracteres que pode ser interpretada como um número|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|Um tipo de referência \(como uma sequência de caracteres, matriz, representante ou tipo de classe\)|  
  
 Você pode usar essas funções para evitar enviar um valor inválido para uma operação ou um procedimento.  
  
## Operador TypeOf  
 Você também pode usar o [Operador TypeOf](../../../../visual-basic/language-reference/operators/typeof-operator.md) para determinar se uma variável objeto no momento se refere a um tipo de dados específico.  A expressão `TypeOf`... `Is` avalia `True` se o tipo em tempo de execução do operando é derivado de ou implementa o tipo especificado.  
  
 O exemplo a seguir usa `TypeOf` em variáveis de objeto referindo\-se a tipos de referência e valor.  
  
```  
' The following statement puts a value type (Integer) in an Object variable.  
Dim num As Object = 10  
' The following statement puts a reference type (Form) in an Object variable.  
Dim frm As Object = New Form()  
If TypeOf num Is Long Then Debug.WriteLine("num is Long")  
If TypeOf num Is Integer Then Debug.WriteLine("num is Integer")  
If TypeOf num Is Short Then Debug.WriteLine("num is Short")  
If TypeOf num Is Object Then Debug.WriteLine("num is Object")  
If TypeOf frm Is Form Then Debug.WriteLine("frm is Form")  
If TypeOf frm Is Label Then Debug.WriteLine("frm is Label")  
If TypeOf frm Is Object Then Debug.WriteLine("frm is Object")  
```  
  
 O exemplo anterior grava na janela **Debug** as seguintes linhas:  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 O variável objeto `num` refere\-se a dados do tipo `Integer`, e `frm` se refere a um objeto da classe <xref:System.Windows.Forms.Form>.  
  
## Matrizes de Objetos  
 Você pode declarar e usar uma matriz de variáveis `Object`.  Isso é útil quando você precisar manipular uma variedade de tipos de dados e classes de objeto.  Todos os de elementos em uma matriz devem ter o mesmo tipo de dados declarado.  Declarar esse tipo de dados como `Object` lhe permite armazenar objetos e instâncias de classe junto com outros tipos de dados na matriz.  
  
## Consulte também  
 [Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Declaração de variável do objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [Atribuição de variável do objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)   
 [Como fazer referência à instância atual de um objeto](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)   
 [Como determinar a que tipo uma variável de objeto se refere](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)   
 [Como determinar se dois objetos estão relacionados](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)   
 [Como determinar se dois objetos são idênticos](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)   
 [Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)