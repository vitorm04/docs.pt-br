---
title: "Delegados (Visual Basic) | Microsoft Docs"
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
  - "delegados [Visual Basic]"
  - "código do Visual Basic, delegados"
ms.assetid: 410b60dc-5e60-4ec0-bfae-426755a2ee28
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Delegados (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Representantes são objetos que se referem aos métodos.  Às vezes, eles são descritos como  *função de tipo seguro ponteiros*  porque eles são semelhante à função ponteiros usados em outras linguagens de programação.  Mas diferentemente ponteiros de função, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] Delegados são um tipo de referência com base na classe <xref:System.Delegate?displayProperty=fullName> de.  Representantes podem fazer referência ambos os métodos compartilhados — os métodos que podem ser chamados sem uma instância específica de uma classe — e instância métodos.  
  
## Eventos e representantes  
 Delegados são úteis em situações em que é necessário um intermediário entre um procedimento de chamada e o Procedimento sendo chamado.  Por exemplo, você pode querer um objeto que gera eventos para poder chamar manipuladores de eventos diferentes em diferentes circunstâncias.  Infelizmente, o objeto aumentando os eventos não se pode saber com antecedência qual manipulador de eventos está tratando um evento específico.  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]permite que você os manipuladores de eventos de associar dinamicamente com eventos, criando um delegado para você quando você usa o `AddHandler` instrução.  Em tempo de execução, o representante encaminha chamadas para o manipulador de eventos apropriado.  
  
 Embora você possa criar seus próprios representantes, na maioria dos casos [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] cria o representante e cuida dos detalhes para você.  Por exemplo, uma instrução `Event` implicitamente define uma classe delegate chamada `<EventName>EventHandler` como uma classe aninhada da classe que contém a instrução `Event` e com a mesma assinatura do evento.  O `AddressOf` instrução implicitamente cria uma instância de um delegado que se refere a um procedimento específico.  As duas linhas de código a seguir são equivalentes.  Na primeira linha, você vê a criação explícita de uma instância de `Eventhandler`, com uma referência para o método `Button1_Click` enviado como o argumento.  A segunda linha é uma forma mais conveniente para fazer a mesma coisa.  
  
 [!code-vb[VbVbalrDelegates#6](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegates_1.vb)]  
  
 Você pode usar a forma abreviada maneira de criar representantes em qualquer lugar o compilador pode determinar o contexto o representante do tipo.  
  
## Declarando eventos que usam um tipo delegate existente  
 Em algumas situações, convém declarar um evento para usar um tipo delegate existente como seu representante subjacente.  A sintaxe a seguir demonstra como:  
  
 [!code-vb[VbVbalrDelegates#7](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegates_2.vb)]  
  
 Isso é útil quando você deseja rotear vários eventos para o mesmo manipulador.  
  
## Representante variáveis e parâmetros  
 Você pode usar representantes para outro, sem eventos relacionados a tarefas, tais como segmentação livre ou com procedimentos que precisarão chamar as versões diferentes de funções em tempo de execução.  
  
 Por exemplo, suponha que você tenha um aplicativo classified\-AD que inclui um caixa de listagem com os nomes dos carros.  Os anúncios são classificados por título, que é normalmente a marca do carro.  Você pode enfrentar um problema ocorre quando alguns carros incluem o ano do carro antes de tornar.  O problema é que a funcionalidade interna de classificação de caixa de listagem classifica somente por códigos de caracteres; ele coloca todos os anúncios começando com datas primeiro, seguido de anúncios começando com o fabricante.  
  
 Para corrigir isso, você pode criar um procedimento de classificação em uma classe que usa a classificação alfabética padrão na maioria das caixas de listagem, mas é possível alternar para o procedimento de classificação personalizada para anúncios de carro em tempo de execução.  Para fazer isso, você passar o procedimento de classificação personalizada para a classe Classificação em tempo de execução, com delegates.  
  
## AddressOf e expressões Lambda  
 Cada classe de delegados define um construtor que passa a especificação a um método objeto.  Um argumento para um construtor delegate deve ser uma referência a um método ou um expressão lambda.  
  
 Para especificar uma referência a um método, use a seguinte sintaxe:  
  
 `AddressOf` \[`expression`.\]`methodName`  
  
 O compile\-time type do `expression` deve ser o nome de uma classe ou uma interface que contém um método do nome especificado cuja assinatura coincide com a assinatura de classe Delegate.  O `methodName` pode ser um método compartilhado ou um método de instância.  `methodName` não é opcional, mesmo se você criar um representante para o método padrão da classe.  
  
 Para especificar um expressão lambda, use a seguinte sintaxe:  
  
 `Function`\(`parm` As `type`, `parm2` As `type2`, ...\]\)`expression`  
  
 O exemplo a seguir mostra que ambos `AddressOf` e expressões lambda, usadas para especificar a referência para um representante.  
  
 [!code-vb[VbVbalrDelegates#15](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegates_3.vb)]  
  
 A assinatura de função deve corresponder do tipo delegate.  Para obter mais informações sobre expressões lambda, consulte [Expressões lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  Para obter mais exemplos de expressão lambda e `AddressOf` atribuições aos delegados, consulte [Conversão de delegado reduzida](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## Tópicos relacionados  
  
|Título|Descrição|  
|------------|---------------|  
|[Como invocar um método delegado](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)|Fornece um exemplo que mostra como associar um método um delegado e depois chama esse método através do delegado.|  
|[Como passar procedimentos para outro procedimento no Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)|Demonstra como usar delegates para passar um procedimento para um outro procedimento.|  
|[Conversão de delegado reduzida](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)|Descreve como você pode atribuir sub\-rotinas e funções a delegados ou manipuladores mesmo quando suas assinaturas não são idênticas|  
|[Eventos](../../../../visual-basic/programming-guide/language-features/events/events.md)|Fornece uma visão geral dos eventos em Visual Basic.|