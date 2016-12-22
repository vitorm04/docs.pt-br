---
title: "Como definir v&#225;rias vers&#245;es de um procedimento (Visual Basic) | Microsoft Docs"
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
  - "sobrecarga de procedimento, várias versões"
  - "procedimentos, definindo"
  - "procedimentos, várias versões"
  - "procedimentos, sobrecarga"
  - "código do Visual Basic, procedimentos"
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como definir v&#225;rias vers&#245;es de um procedimento (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Explica como definir um procedimento em múltiplas versões *sobrecarregando\-o*, usando o mesmo nome mas uma diferente lista de parâmetro para cada versão.  O objetivo de sobrecarga é definir várias versões intimamente relacionadas a um procedimento sem diferenciá\-los pelo nome.  
  
 Para obter mais informações, consulte [Sobrecarga de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).  
  
### Como: definir várias versões de um procedimento  
  
1.  Grave uma afirmação de declaração `Sub` ou `Function` para cada versão do procedimento que você deseja definir.  Use o mesmo nome do procedimento em toda declaração.  
  
2.  Preceder a palavra\-chave `Sub` ou `Function` em cada declaração com a palavra\-chave [Sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md).  Você pode omitir `Overloads` opcionalmente nas declarações, mas se você incluí\-lo em qualquer um das declarações, você deve incluí\-lo em cada declaração.  
  
3.  Após cada instrução de declaração, grave o código procedimento para manipular a ocorrência específica onde o código de chamada fornece argumentos correspondentes a lista de parâmetros desta versão.  Você não precisará testar para quais parâmetros o código de chamada tenha fornecido.  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]passa o controle para a versão correspondente do seu procedimento.  
  
4.  Cada versão do procedimento com a declaração `End Sub` ou `End Function` conforme apropriado.  
  
## Exemplo  
 O exemplo a seguir define um procedimento `Sub` para lançar uma transação contra um saldo do cliente.  Ele usa a palavra\-chave `Overloads` para definir duas versões do procedimento, uma que aceita o cliente por nome e a outra pelo número de conta.  
  
 [!code-vb[VbVbcnProcedures#72](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-define-multiple-versions-of-a-procedure_1.vb)]  
  
 O código de chamada pode obter a identificação do cliente como um `String` ou um `Integer` e use a mesma instrução de chamada em ambos os casos.  
  
 Para obter informações sobre como chamar essas versões do procedimento `post`, consulte [Como chamar um procedimento sobrecarregado](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-overloaded-procedure.md).  
  
## Compilando o código  
 Verifique se que cada uma das suas versões sobrecarregadas tem o mesmo nome do procedimento, mas uma lista de parâmetros diferentes.  
  
## Consulte também  
 [Procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Parâmetros e argumentos de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Solucionando problemas de procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)   
 [Como sobrecarregar um procedimento que usa parâmetros opcionais](../Topic/How%20to:%20Overload%20a%20Procedure%20that%20Takes%20Optional%20Parameters%20\(Visual%20Basic\).md)   
 [Como sobrecarregar um procedimento que usa um número indefinido de parâmetros](../../../../visual-basic/programming-guide/language-features/procedures/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)   
 [Considerações sobre procedimentos de sobrecarga](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)   
 [Resolução de sobrecarga](../../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)