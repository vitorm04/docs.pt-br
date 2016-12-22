---
title: "Subprocedimentos (Visual Basic) | Microsoft Docs"
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
  - "procedimentos, Chamando "
  - "procedimentos, Sub"
  - "blocos de instrução"
  - "Subprocedimentos"
  - "Subprocedimentos, sobre subprocedimentos"
  - "Subprocedimentos, Chamando "
  - "Subprocedimentos, sintaxe"
  - "sintaxe, Subprocedimentos"
ms.assetid: 6a0a4958-ed0a-4d3d-8d31-0772c82bda58
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Subprocedimentos (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Um `Sub`procedimento é uma série de[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] declarações anexado pelo `Sub`e por `End Sub`declarações.  O `Sub` procedimento realiza uma tarefa e então retorna controle ao código de chamada, mas não retorna um valor ao código de chamada.  
  
 Cada vez que é feita uma chamada de procedimento, suas declarações são executadas, começando pela primeira declaração executável depois da `Sub` declaração e finalizando com o primeiro `End Sub`,`Exit Sub`, ou  declaração`Return` encontrada.  
  
 Você pode definir um `Sub`procedimento em módulos, classes e estruturas.  Por padrão, é `Public`, o que significa que você pode chamá\-lo de qualquer lugar no seu aplicativo que acessou o módulo, classe ou estrutura na qual você a definiu.  O termo *método* descreve um procedimento`Sub` ou `Function` que é acessado de fora de seu módulo definidor, classe ou estrutura.  Para obter mais informações, consulte [Procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/index.md).  
  
 Um procedimento `Sub` pode receber argumentos, como constantes, variáveis ou expressões, que são passadas a ele pelo código de chamada.  
  
## Sintaxe da Declaração  
 A sintaxe para declarar um `Sub` procedimento é como se segue:  
  
 `[` *modifiers* `] Sub`  *subname* `[(` *parameterlist* `)]`  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 O `modifiers` podem especificar o nível de acesso e informações sobre sobrecarregamento, desautorizações, compartilhamento e sombreamento.  Para obter mais informações, consulte [Instrução Sub](../../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## Declaração de parâmetros  
 Você declara cada parâmetro de procedimento similarmente a como você declara uma variável, especificando o nome do parâmetro e o tipo dos dados.  Você pode, também, especificar o mecanismo de passagem, e se o parâmetro é opcional ou uma matriz de parâmetros.  
  
 A sintaxe para cada parâmetro na lista de parâmetros é como se segue:  
  
 `[Optional] [ByVal | ByRef] [ParamArray]`  *ParameterName*  `As`  *tipo de dados*  
  
 Se o parâmetro é opcional, você deve também fornecer um valor padrão como parte de sua declaração.  A sintaxe para especificar um valor padrão é como se segue:  
  
 `Optional [ByVal | ByRef]`  *ParameterName*  `As`  *tipo de dados*  `=`  *defaultvalue*  
  
### Parâmetros como variáveis locais  
 Quando o controle passa para o procedimento, cada parâmetro é tratado como uma variável local.  Isso significa que seu tempo de vida é o mesmo que o do procedimento, e seu escopo é o procedimento inteiro.  
  
## Sintaxe de Chamada  
 Você invocar um `Sub` procedimento explicitamente com uma declaração de chamada que permanece sozinha.  Você não pode chamá\-lo usando seu nome numa expressão.  Você deve fornecer valores para todos os argumentos que não são opcionais, e você precisa cercar a lista de argumentos entre parênteses.  Se nenhum argumento é fornecido, você pode, opcionalmente, omitir os parênteses.  O uso do `Call` teclado é opcional, mas não é recomendado.  
  
 A sintaxe para chamar um procedimento `Sub` é o seguinte:  
  
 `[Call]`  *subname* `[(` *Listadeargumentos* `)]`  
  
 Você pode chamar um método `Sub` de fora da classe que a define.  Primeiramente, você tem de usar o teclado `New` para criar um exemplo da classe, ou chamar um método que retorna um exemplo da classe.  Para obter mais informações, consulte [Operador New](../../../../visual-basic/language-reference/operators/new-operator.md).  Então, você pode usar a seguinte sintaxe para chamar o método `Sub` no objeto de exemplo.  
  
 *Objeto*,*nome do método*`[(`*lista de argumentos*`)]`  
  
### Ilustração de Declaração e Chamada  
 O seguinte procedimento `Sub` manda o operador do computador qual tarefa de aplicativo está prestes a executar, e também exibe um carimbo de data\/hora.  Em vez de duplicar este código no início de toda tarefa, o aplicativo apenas chama  `tellOperator`  de várias localizações.  Cada chamada passa uma string no argumento do  `task`  que identifica que a tarefa está sendo iniciada.  
  
 [!code-vb[VbVbcnProcedures#2](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/sub-procedures_1.vb)]  
  
 O exemplo a seguir mostra uma chamada típica a `tellOperator`.  
  
 [!code-vb[VbVbcnProcedures#3](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/sub-procedures_2.vb)]  
  
## Consulte também  
 [Procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedimentos de função](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Procedimentos de propriedade](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Procedimentos do operador](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Parâmetros e argumentos de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Instrução Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Como chamar um procedimento que não retorne um valor](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-procedure-that-does-not-return-a-value.md)   
 [Como chamar um manipulador de eventos no Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-event-handler.md)