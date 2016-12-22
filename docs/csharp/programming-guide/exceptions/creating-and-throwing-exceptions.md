---
title: "Criando e lan&#231;ando exce&#231;&#245;es (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "capturando exceções [C#]"
  - "exceções [C#], criando"
  - "exceções [C#], lançando"
  - "lançando exceções [C#]"
ms.assetid: 6bbba495-a115-4c6d-90cc-1f4d7b5f39e2
caps.latest.revision: 28
caps.handback.revision: 28
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Criando e lan&#231;ando exce&#231;&#245;es (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Exceções são usadas para indicar que um erro ocorreu durante a execução do programa.  Objetos de exceção que descrevem um erro são criados e, em seguida  *lançada* com o  [lança](../../../csharp/language-reference/keywords/throw.md) palavra\-chave.  O tempo de execução, em seguida, pesquisa o manipulador de exceção mais compatível.  
  
 Os programadores devem lançar exceções quando uma ou mais das condições a seguir são verdadeiras:  
  
-   O método não pode concluir sua funcionalidade definida.  
  
     Por exemplo, se um parâmetro para um método tem um valor inválido:  
  
     [!code-cs[csProgGuideExceptions#12](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_1.cs)]  
  
-   É feita uma chamada inadequada a um objeto, com base no estado do objeto.  
  
     Um exemplo é tentar gravar em um arquivo somente leitura de leitura.  Em casos onde o estado de um objeto não permite uma operação, lançar uma instância de <xref:System.InvalidOperationException> ou um objeto com base em uma derivação dessa classe.  Este é um exemplo de um método que lança um <xref:System.InvalidOperationException> objeto:  
  
     [!code-cs[csProgGuideExceptions#13](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_2.cs)]  
  
-   Quando um argumento para um método causa uma exceção.  
  
     Nesse caso, a exceção original deve ser detectada e um <xref:System.ArgumentException> instância deve ser criada.  A exceção original deve ser passada para o construtor da <xref:System.ArgumentException> como o <xref:System.Exception.InnerException%2A> parâmetro:  
  
     [!code-cs[csProgGuideExceptions#14](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_3.cs)]  
  
 Exceções contém uma propriedade chamada <xref:System.Exception.StackTrace%2A>.  Esta string contém o nome dos métodos na pilha de chamadas atual, juntamente com o número de linha e o nome do arquivo onde a exceção foi lançada para cada método.  A <xref:System.Exception.StackTrace%2A> objeto é criado automaticamente pelo common language runtime \(CLR\) do ponto da `throw` instrução, para que as exceções devem ser lançadas desde o ponto em que o rastreamento de pilha deve começar.  
  
 Todas as exceções contém uma propriedade chamada <xref:System.Exception.Message%2A>.  Essa seqüência de caracteres deve ser definida para explicar o motivo da exceção.  Observe que as informações que são sensíveis à segurança não devem ser colocadas no texto da mensagem.  Além das <xref:System.Exception.Message%2A>, <xref:System.ArgumentException> contém uma propriedade chamada <xref:System.ArgumentException.ParamName%2A> que deve ser definida como o nome do argumento que causou a exceção seja lançada.  No caso de um setter de propriedade, <xref:System.ArgumentException.ParamName%2A> deve ser definida como `value`.  
  
 Membros de métodos public e protected devem lançar exceções, sempre que eles não é possível concluir suas funções pretendidas.  A classe de exceção que é lançada deve ser a exceção mais específica disponível que atenda às condições de erro.  Essas exceções devem ser documentadas como parte da funcionalidade de classe e classes derivadas ou atualizações para a classe original devem reter o mesmo comportamento para compatibilidade com versões anteriores.  
  
## Procedimentos para evitar que ao gerar exceções  
 A lista a seguir identifica as práticas recomendadas para evitar ao gerar exceções:  
  
-   Exceções não devem ser usadas para alterar o fluxo de um programa como parte da execução comum.  Exceções só devem ser usadas para relatar e manipular condições de erro.  
  
-   Exceções não devem ser retornadas como um valor de retorno ou parâmetro, em vez de ser lançada.  
  
-   Não jogue a <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName>, <xref:System.NullReferenceException?displayProperty=fullName>, ou <xref:System.IndexOutOfRangeException?displayProperty=fullName> intencionalmente a partir de seu próprio código fonte.  
  
-   Não crie exceções que podem ser geradas no modo de depuração, mas não o modo de versão.  Para identificar erros de tempo de execução durante a fase de desenvolvimento, use depurar Assert.  
  
## Definir Classes de exceção  
 Programas podem lançar uma classe de exceção predefinidos na <xref:System> namespace \(exceto onde observado anteriormente\), ou criar suas próprias classes de exceção, derivando de <xref:System.Exception>.  As classes derivadas devem definir pelo menos quatro construtores: construtor um padrão, uma que define a propriedade de mensagem e uma que define ambas as <xref:System.Exception.Message%2A> e <xref:System.Exception.InnerException%2A> propriedades.  O quarto construtor é usado para serializar a exceção.  Novas classes de exceção devem ser serializáveis.  Por exemplo:  
  
 [!code-cs[csProgGuideExceptions#15](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_4.cs)]  
  
 Novas propriedades só devem ser adicionadas à classe de exceção quando os dados que elas fornecem são úteis para resolver a exceção.  Se novas propriedades forem adicionadas à classe derivada de exceção, `ToString()` deve ser substituído para retornar as informações adicionadas.  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Exceções e manipulação de exceções](../../../csharp/programming-guide/exceptions/exceptions-and-exception-handling.md)   
 [Hierarquia de exceções](../Topic/Exception%20Hierarchy.md)   
 [Manipulação de exceções](../../../csharp/programming-guide/exceptions/exception-handling.md)