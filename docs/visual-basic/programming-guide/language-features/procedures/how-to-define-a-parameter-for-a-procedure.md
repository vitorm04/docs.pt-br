---
title: "Como definir um par&#226;metro para um procedimento (Visual Basic) | Microsoft Docs"
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
  - "parâmetros de procedimento, definindo"
  - "parâmetros de procedimento, definindo tipos de dados para"
  - "procedimentos, definindo"
  - "procedimentos, parâmetros"
  - "código do Visual Basic, procedimentos"
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como definir um par&#226;metro para um procedimento (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Um *parâmetro* permite que o código passe um valor ao procedimento quando ele o chama.  Você declara cada parâmetro para um procedimento da mesma maneira que você declara uma variável, especificand seu nome e tipo de dados.  Você também especifica o mecanismo passante, e se o parâmetro é opcional.  
  
 Para obter mais informações, consulte [Parâmetros e argumentos de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md).  
  
### Para definir um parâmetro de procedimento  
  
1.  Na declaração de procedimento, adicione o nome de parâmetro à lista de parâmetros do procedimento, separando\-o  de outros parâmetros por vírgulas.  
  
2.  Decida o tipo de dados do parâmetro.  
  
3.  Siga  nome do parâmetro com uma cláusula `As` para especificar o tipo de dados.  
  
4.  Decida o mecanismo passante que você deseja para o parâmetro.  Normalmente você passa um parâmetro por valor, a não ser que você deseje que o procedimento seja capaz de alterar seu valor no código de chamada.  
  
5.  Preceda o nome de parâmetro por [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) para especificar o mecanismo passante.  Para obter mais informações, consulte [Diferenças entre passar um argumento por valor e por referência](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
6.  Se o parâmetro for opcional, preceda o mecanismo passante por [Opcional](../../../../visual-basic/language-reference/modifiers/optional.md) e siga o tipo de dados do parâmetro por um snal de igual \(`=`\) e um valor padrão.  
  
     O exemplo a seguir define linhas gerais de um procedimento `Sub` com três parâmetros.  Os dois prmeiros são exigidos e o terceiro é opcional.  As declarações de parâmetro são separadas na lista de parâmetros por vírgulas.  
  
     [!code-vb[VbVbcnProcedures#33](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-define-a-parameter-for-a-procedure_1.vb)]  
  
     O prieiro parâmetro aceita um objeto  `customer` , e `updateCustomer` pode atualizar a variável diretamente passada ao `c` porque o argumento é passado [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).  O procedimento não pode alterar os valores dos dois últimos argumentos porque eles são passados [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).  
  
     Se o código de chamada não fornece um valor para o parâmetro  `level` , [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] o configura para o valor padrão 0.  
  
     Se o onterruptor de verificação de tipo \([Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)\) está na posição `Off`, a cláusula `As` é opcionak quando você define um parâmetro.  Entretanto, se qualquer outro parâmetro usa uma cláusula `As`, todos eles devem usar.  Se o interruptor de verificação de tipo estiver na posi;cão `On`, a cláusula `As` é exigida para toda definição de parâmetro.  
  
     Especificar tipos de dados para todos os seus elementos de programação é conhecido como *tipagem forte*.  Quando você estabelece `Option Strict On`, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] faz cumprir a tipagem forte.  Isso é fortemente recomendado, pelas seguintes razões:  
  
    -   Ele ativa suporte IntelliSense para suas variáveis e parâmetros.  Isto permite que você veja suas propriedades e outros membros à medida que você digita no seu código.  
  
    -   Isso permite que o compilador efetue verificação de tipos.  Isso ajuda a obter declarações que podem falhar no momento de execução devido a erros como overflow.  Isso também obtém chamadas a métodos em objetos que não os suportam.  
  
    -   Isso resulta em execução mais rápida do seu código.  Uma razão para isso é que se você não especificar um tipo de dados para um elemento de programação, o compilador [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] designa\-o o tipo `Object`.  Seu código compilado pode ter de compilar entre `Object` e outros tipos de dados e vice\-versa, o que reduz desempenho.  
  
## Consulte também  
 [Procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Subprocedimentos](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Procedimentos de função](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Como passar argumentos para um procedimento](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [Passando argumentos por valor e por referência](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Procedimentos recursivos](../../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)   
 [Sobrecarga de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Objetos e classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Programação orientada a objeto](../Topic/Object-Oriented%20Programming%20\(C%23%20and%20Visual%20Basic\).md)