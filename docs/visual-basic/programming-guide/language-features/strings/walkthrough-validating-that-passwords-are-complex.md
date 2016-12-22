---
title: "Instru&#231;&#245;es passo a passo: validando senhas complexas (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "tipo de dados String, validação"
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#245;es passo a passo: validando senhas complexas (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este método verifica a existência de algumas características de senhas robustas e atualiza um parâmetro de string com informações sobre em quais quesitos a senha falha.  
  
 Senhas podem ser usadas num sistema seguro para autenticar um usuário.  Entretanto, as senhas não devem ser facilmente adivinhadas por usuários não autorizados.  Invasores podem usar um programa de *Dictionary Attack*, que faz iterações através de todas as palvras num dicionário \(ou vários dicionários em linguagens diferentes\) e teste se alguma das palavras funciona como senha de usuário.  Senhas frágeis como "Yankees" ou "Mustang" podem ser adivinhadas facilmente.  Senhas robustas, como "?You'L1N3vaFiNdMeyeP@sSWerd\!", são muito menos prováveis de serem adivinhadas.  Um sistema protegido por senha deve assegurar que usuários escolham senhas robustas.  
  
 Uma senha robusta é complexa \(contendo uma mistura de letras maiúsculas, minúsculas, números e caracteres especiais\) e não é uma palavra.  Este exemplo demonstra como verificar a complexidade das senhas.  
  
## Exemplo  
  
### Código  
 [!code-vb[VbVbcnRegEx#1](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/walkthrough-validating-that-passwords-are-complex_1.vb)]  
  
## Compilando o código  
 Chame este mtodo passando a string que contém a senha.  
  
 Este exemplo requer:  
  
-   Acesso aos membros do espaço de nomes <xref:System.Text.RegularExpressions>.  Adicione uma declaração `Imports` se você não está qualificando completamente os nomes de membros em seu código.  Para obter mais informações, consulte [Instrução Imports \(tipo e namespace .NET\)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## Segurança  
 Se você está movimento a senha numa rede, você precisa usar um método seguro para transferência de dados.  Para obter mais informações, consulte [ASP.NET Web Application Security](../Topic/ASP.NET%20Web%20Application%20Security.md).  
  
 Você pode aumentar a precisão da função `ValidatePassword` adicionando verificações de complexidade adicionais:  
  
-   Compare a senha e suas substrings com o nome do usuário, seu ID, e com um dicionário definido pelo aplicativo.  Além disso, trate caracteres visualmente similares como equivalentes quando fizer as comparações.  Por exemplo, trate as letras "l" e "e" como equivalentes aos numerais "1" e "3".  
  
-   Se há apenas um caractere maiúsculo, garanta que não é o primeiro caractere do password.  
  
-   Garanta que os dois últimos caracteres da senha são letras.  
  
-   Não permita senhas nas quais todos os símbolos inseridos são da linha de cima do teclado.  
  
## Consulte também  
 <xref:System.Text.RegularExpressions.Regex>   
 [ASP.NET Web Application Security](../Topic/ASP.NET%20Web%20Application%20Security.md)