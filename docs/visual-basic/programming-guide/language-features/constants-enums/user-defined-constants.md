---
title: "Constantes definidas pelo usu&#225;rio (Visual Basic) | Microsoft Docs"
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
  - "referências circulares entre constantes"
  - "instrução Const [Visual Basic], constantes definidas pelo usuário"
  - "constantes, referências circulares"
  - "constantes, definido pelo usuário"
  - "escopo, constantes"
  - "constantes definidas pelo usuário"
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Constantes definidas pelo usu&#225;rio (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Uma constante é um nome com significado que toma o lugar de um número ou string que não muda.  Constantes armazenam valores que, como o nome diz, permanecem os mesmos durante a execução de um aplicativo.  Você pode usar constantes que são definidas por controles ou componentes com os quais você trabalha, ou você pode criar suas próprias.  Constantes que você mesmo cria são descritas como  *definido pelo usuário* .  
  
 Você declarar uma constante com a instrução `Const`, usando as mesmas diretrizes que você faria para criar um nome de variável.  Se a opção `Option Strict` estiver `On`, você deve explicitar o tipo da constante.  
  
## Uso da Instrução Const  
 Uma declaração `Const` pode representar uma quantidade matemática ou data\/tempo:  
  
 [!code-vb[VbEnumsTask#10](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_1.vb)]  
  
 Ele também pode definir constantes `String`:  
  
 [!code-vb[VbEnumsTask#13](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_2.vb)]  
  
 A expressão no lado direito da sinal de igualdade \(`=`\) é geralmente um número ou sequência literal, mas também pode ser uma expressão que resulta em um número ou sequência de caracteres \(embora essa expressão não pode conter chamadas a funções\).  Você pode até mesmo definir constantes em termos de constantes definidas anteriormente:  
  
 [!code-vb[VbEnumsTask#15](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_3.vb)]  
  
## Escopo de Constantes Definidas pelo Usuário  
 Um escopo de uma declaração  `Const` é o mesmo da variável declarada no mesmo local.  Você pode especificar escopo em qualquer uma das seguintes maneiras:  
  
-   Para criar uma constante que existe somente dentro de um procedimento, declare\-a dentro desse procedimento.  
  
-   Para criar uma constante disponível para todos os procedimentos em uma classe, mas não para qualquer código fora desse módulo, declare\-lo na seção declarações de classe.  
  
-   Para criar uma constante que está disponível para todos os membros de um conjunto de módulos \(assembly\), mas não para clientes fora do conjunto de módulos \(assembly\), declare\-a usando a palavra\-chave `Friend` na seção declarações da classe.  
  
-   Para criar uma constante que é disponível em todo o aplicativo, declare\-a usando a palavra\-chave `Public` na seção de declarações da classe.  
  
 Para obter mais informações, consulte [Como declarar uma constante](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).  
  
### Evitando Referências Circulares  
 Como constantes podem ser definidas em termos de outras constantes, é possível criar inadvertidamente um *ciclo* , ou referência circular, entre duas ou mais constantes.  Um ciclo ocorre quando você tem duas ou mais constantes públicas, cada uma deles é definida em termos da outra, como no exemplo a seguir:  
  
 [!code-vb[VbEnumsTask#16](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_4.vb)]  
[!code-vb[VbEnumsTask#17](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_5.vb)]  
  
 Se ocorrer um ciclo, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] gera um erro do compilador.  
  
## Consulte também  
 [Instrução Const](../../../../visual-basic/language-reference/statements/const-statement.md)   
 [Tipos de dados constante e literal](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)   
 [Constantes e enumerações](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)   
 [Constantes e enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md)   
 [Visão geral de enumerações](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)   
 [Visão geral de constantes](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [Como declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [Enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)