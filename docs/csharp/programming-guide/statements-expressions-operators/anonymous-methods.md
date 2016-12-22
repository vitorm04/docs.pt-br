---
title: "M&#233;todos an&#244;nimos (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "métodos anônimos [C#]"
  - "delegados [C#], métodos anônimos"
  - "métodos [C#], anônimos"
ms.assetid: a62441fa-f0a3-4acb-9aa6-93762a635275
caps.latest.revision: 31
caps.handback.revision: 31
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# M&#233;todos an&#244;nimos (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Nas versões do C\# antes de 2.0, a única maneira de declarar um  [delegar](../../../csharp/language-reference/keywords/delegate.md) foi usar  [chamado métodos](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md).  C\# 2.0 introduziu métodos anônimos e no C\# 3.0 e posterior, as expressões lambda substituem métodos anônimos como a melhor maneira de escrever código embutido.  No entanto, as informações sobre os métodos anônimos neste tópico também se aplica a expressões lambda.  Há um caso em que um método anônimo fornece funcionalidade não encontrada em expressões lambda.  Métodos anônimos permitem omitir a lista de parâmetro.  Isso significa que um método anônimo pode ser convertido para representantes com uma variedade de assinaturas.  Não é possível com as expressões lambda.  Para obter mais informações especificamente sobre expressões lambda, consulte [Expressões lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 Criar métodos anônimos é essencialmente uma forma de passar um bloco de código como um parâmetro delegado.  Aqui estão dois exemplos:  
  
 [!code-cs[csProgGuideDelegates#6](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_1.cs)]  
  
 [!code-cs[csProgGuideDelegates#5](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_2.cs)]  
  
 Usando os métodos anônimos, reduzir a sobrecarga codificação instanciar delegates porque você não precisará criar um método separado.  
  
 Por exemplo, especificar que um bloco de código em vez de um delegado pode ser útil em uma situação quando precisar criar um método pode parecer uma sobrecarga desnecessária.  Um bom exemplo seria quando você iniciar um novo thread.  Essa classe cria um segmento e também contém código que executa o thread sem criar um método adicional para o delegado.  
  
 [!code-cs[csProgGuideDelegates#7](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_3.cs)]  
  
## Comentários  
 O escopo dos parâmetros de um método anônimo é o  *Bloco de método anônimo*.  
  
 É um erro ter uma instrução de salto, como  [goto](../../../csharp/language-reference/keywords/goto.md),  [quebra](../../../csharp/language-reference/keywords/break.md), ou  [continuar](../../../csharp/language-reference/keywords/continue.md), dentro do bloco de método anônimo se o destino estiver fora do bloco.  Também é um erro ter uma instrução de salto, como `goto`, `break`, ou `continue`, fora do bloco de método anônimo se o destino estiver dentro do bloco.  
  
 Variáveis locais e parâmetros cujo escopo contém uma declaração de método anônimo são chamados  *externo* variáveis de método anônimo.  Por exemplo, no segmento de código a seguir, `n` é uma variável externa:  
  
 [!code-cs[csProgGuideDelegates#8](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_4.cs)]  
  
 Uma referência à variável externa `n` deve ser  *capturado* quando o delegado é criado.  Ao contrário das variáveis locais, a vida útil de uma variável capturada estende até os representantes que fazem referência os métodos anônimos são qualificados para coleta de lixo.  
  
 Um método anônimo não pode acessar o  [ref](../../../csharp/language-reference/keywords/ref.md) ou  [out](../../../csharp/language-reference/keywords/out.md) parâmetros de um escopo externo.  
  
 Nenhum código não seguro pode ser acessado dentro do  *Bloco de método anônimo*.  
  
 Métodos anônimos não são permitidos no lado esquerdo do  [é](../../../csharp/language-reference/keywords/is.md) operador.  
  
## Exemplo  
 O exemplo a seguir demonstra duas maneiras de instanciar um delegate:  
  
-   Associando o delegado com um método anônimo.  
  
-   Associando o delegado um método nomeado \(`DoWork`\).  
  
 Em cada caso, uma mensagem é exibida quando o delegado é chamado.  
  
 [!code-cs[csProgGuideDelegates#4](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_5.cs)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Delegados](../../../csharp/programming-guide/delegates/index.md)   
 [Expressões lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
 [Código não seguro e ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [Métodos](../../../fsharp/language-reference/members/methods.md)   
 [Delegados com métodos nomeados versus anônimos](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)