---
title: "Uso eficiente de tipos de dados (Visual Basic) | Microsoft Docs"
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
  - "Função AscW, preferido para Asc"
  - "Função ChrW, preferido para Chr"
  - "tipos de dados [Visual Basic], otimizando"
  - "tipos de dados [Visual Basic], tipagem forte"
  - "tipos de dados [Visual Basic], uso eficiente"
  - "tipos de dados [Visual Basic], tipificação fraca"
  - "otimização, tipos de dados"
  - "desempenho, eficiência de tipos de dados"
  - "tipagem forte"
  - "tipificação, forte"
ms.assetid: 28f5e4ba-ec24-4f37-b90a-e8ee822f778a
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Uso eficiente de tipos de dados (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Variáveis não declaradas e declaradas sem um tipo de dados são atribuídas ao tipo de dados `Object`.  Isso facilita escrever programas rapidamente, mas pode fazer com que sejam executados mais lentamente.  
  
## Tipagem Forte  
 Especificar tipos de dados para todas as variáveis é um técnica conhecida como  *tipagem fote* .  Usar tipagem forte apresenta diversas vantagens:  
  
-   Permite suporte IntelliSense para suas variáveis.  Isso permite que você veja suas propriedades e outros membros conforme você digita em código.  
  
-   Ele aproveita a verificação de tipo do compilador.  E captura instruções que podem falhar em tempo de execução devido a erros como overflow.  Isso também obtém chamadas a métodos em objetos que não os suportam.  
  
-   Isso resulta em execução mais rápida do seu código.  
  
## Tipos de dados mais eficientes  
 Para variáveis que nunca contêm frações, os tipos de dados inteiro são mais eficientes do que os tipos não integrais.  Em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], `Integer` e `UInteger` são os tipos numéricos mais eficientes.  
  
 Para números fracionários, `Double` é o tipo de dados mais eficiente, porque os processadores em plataformas atuais executam operações de ponto flutuante com precisão dupla.  No entanto, operações com `Double` não são tão rápidas como com os tipos integrais como `Integer`.  
  
## Especificar Tipos de Dados  
 Use a [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) para declarar uma variável de um tipo específico.  Você pode especificar simultaneamente seu nível de acesso usando a palavra\-chave[Público](../../../../visual-basic/language-reference/modifiers/public.md), [Protegido](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), ou [Particular](../../../../visual-basic/language-reference/modifiers/private.md), como no exemplo a seguir.  
  
```  
Private x As Double  
Protected s As String  
```  
  
## Conversão de caracteres  
 As funções `AscW` e `ChrW` operam em Unicode.  Você deve usá\-las preferencialmente a `Asc` e `Chr`,que devem traduzir de e para Unicode.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>   
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>   
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>   
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>   
 [Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Tipos de dados numéricos](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)   
 [Declaração de variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Usando IntelliSense](/visual-studio/ide/using-intellisense)