---
title: "Mensagens de erro (Visual Basic) | Microsoft Docs"
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
  - "mensagens de erro"
  - "erros [Visual Basic]"
  - "erros [Visual Basic], interceptável"
  - "erros interceptáveis"
ms.assetid: f2dda05b-baef-41f5-8bb1-598bd7cf239f
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Mensagens de erro (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Quando você gravar, criar, ou executar um aplicativo Visual Basic, os seguintes tipos de erros podem ocorrer:  
  
1.  Erros de tempo de design, que ocorrem quando você escrever um aplicativo no Visual Studio.  
  
2.  Erros de tempo de compilação, que ocorrem quando você compilar um aplicativo no Visual Studio ou em um prompt de comando.  
  
3.  Erros em tempo de execução, que ocorrem quando você executar um aplicativo no Visual Studio ou como um arquivo executável autônomo.  
  
 Para obter informações sobre como solucionar um erro específico, consulte [Recursos adicionais para programadores do Visual Basic](../../../visual-basic/getting-started/additional-resources.md).  
  
## Erros de Tempo de Execução  
 Se um aplicativo Visual Basic tenta executar uma ação que o sistema não pode executar, ocorre um erro em tempo de execução, e gera de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] um objeto de `Exception` .  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] pode gerar erros personalizados de qualquer tipo de dados, incluindo objetos de `Exception` , usando a instrução de `Throw` .  Um aplicativo pode identificar o erro exibir o número do erro e a mensagem de uma exceção capturada.  Se um erro não for detectado, o aplicativo termina.  
  
 o código pode interceptar e examinar erros em tempo de execução.  Se você incluir o código que produz o erro em um bloco de `Try` , você pode capturar qualquer erro gerado em um bloco correspondente de `Catch` .  Para obter informações sobre como interceptar erros em tempo de execução e responder\-lhes em seu código, consulte [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## Erros de tempo de compilação  
 Se o compilador Visual Basic encontrar um problema no código, um erro em tempo de compilação ocorre.  Em o editor de códigos, você pode facilmente identificar qual linha de código causou o erro porque uma linha ondulada aparece sob essa linha de código.  A mensagem de erro aparece se você apontar para a linha subescrita ondulada ou abra **Lista de erros**, que também mostra outras mensagens.  
  
 Se um identificador tem um a linha subescrita ondulada e um sublinhado curto aparece no caractere mais à direita, você pode gerar um stub para a classe, o construtor, o método, a propriedade, o campo ou enum.  Para mais informações, consulte [Gerar a partir do uso](/visual-cpp/misc/generate-from-usage).  
  
 Resolvendo avisos do compilador Visual Basic, você pode ser capaz de gravar o código executado mais rapidamente e com menos erros.  Esses avisos identificam o código que pode causar erros quando o aplicativo é executado.  Por exemplo, o compilador adverte\-o se você tentar invocar um membro de uma variável de objeto não atribuída, retornar de uma função sem definir o valor de retorno, ou executar um bloco de `Try` com erros de lógica para detectar exceções.  Para obter mais informações sobre avisos, incluindo como ou desligá\-los, consulte [Configurando avisos no Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).