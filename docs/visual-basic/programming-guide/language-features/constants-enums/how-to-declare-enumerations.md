---
title: "Como declarar enumera&#231;&#245;es (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "declarações, enumerações"
  - "declarando enumerações"
  - "enumerações [Visual Basic], declarando"
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como declarar enumera&#231;&#245;es (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você cria uma enumeração com o `Enum` a instrução na seção declarações de uma classe ou módulo.  Você não pode declarar uma enumeração dentro de um método.  Para especificar o nível apropriado de acesso, use `Private`, `Protected`, `Friend`, ou `Public`.  
  
 Um `Enum` o tipo tem um nome, um tipo subjacente e um conjunto de campos, cada uma representando uma constante.  O nome deve ser válido [!INCLUDE[vbprvblong](../../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] qualificador.  O tipo subjacente deve ser um dos tipos inteiros —`Byte`, `Short`, `Long` ou `Integer`.  `Integer`é o padrão.  Enumerações são sempre fortemente tipadas e não são intercambiáveis com tipos de número inteiro.  
  
 Enumerações não podem ter valores de ponto flutuante.  Se uma enumeração é atribuída um valor de ponto flutuante com `Option Strict On`, um resulta de erros do compilador.  Se `Option Strict` é `Off`, o valor será automaticamente convertido para o `Enum` tipo.  
  
 Para obter informações sobre nomes e como usar o `Imports` a instrução para tornar a qualificação de nome desnecessário, consulte [Enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
### Para declarar uma enumeração  
  
1.  Escrever uma declaração que inclui um nível de acesso a código, o `Enum` palavra\-chave e um nome válido, como nos exemplos a seguir, cada um deles declara uma diferente `Enum`.  
  
     [!code-vb[VbEnumsTask#3](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_1.vb)]  
  
2.  Defina as constantes na enumeração.  Por padrão, a primeira constante em uma enumeração é inicializada para `0`, e constantes subseqüentes são inicializados para um valor de um mais do que a constante anterior.  Por exemplo, a enumeração seguinte, `Days`, contém uma constante chamada `Sunday` com o valor `0`, uma constante chamada `Monday` com o valor `1`, uma constante chamada `Tuesday` com o valor da `2`e assim por diante.  
  
     [!code-vb[VbEnumsTask#4](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_2.vb)]  
  
3.  Você pode atribuir explicitamente valores constantes em uma enumeração usando uma instrução de atribuição.  Você pode atribuir qualquer valor inteiro, incluindo os números negativos.  Por exemplo, convém constantes com valores menores que zero para representar as condições de erro.  Na enumeração seguinte, a constante `Invalid` explicitamente é atribuído o valor `–1`e a constante `Sunday` recebe o valor `0`.  Porque é a primeira constante na enumeração, `Saturday` também é inicializada com o valor `0`.  O valor de `Monday` é `1` \(mais do que o valor de um `Sunday`\); o valor de `Tuesday` é `2`e assim por diante.  
  
     [!code-vb[VbEnumsTask#5](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_3.vb)]  
  
### Para declarar uma enumeração como um tipo explícito  
  
-   Especificar o tipo do enum usando o `As` cláusula, conforme mostrado no exemplo a seguir.  
  
     [!code-vb[VbEnumsTask#6](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_4.vb)]  
  
## Consulte também  
 [Enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [Como fazer referência a um membro de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)   
 [Como iterar em uma enumeração no Visual Basic](../Topic/How%20to:%20Iterate%20Through%20An%20Enumeration%20in%20Visual%20Basic.md)   
 [Como determinar a cadeia de caracteres associada a um valor de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)   
 [Quando usar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)   
 [Visão geral de constantes](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [Tipos de dados constante e literal](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)   
 [Constantes e enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md)