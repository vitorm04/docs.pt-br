---
title: "Erro na cria&#231;&#227;o de manifesto do assembly: &lt;error message&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30140"
  - "vbc30140"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30140"
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Erro na cria&#231;&#227;o de manifesto do assembly: &lt;error message&gt;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O compilador [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] chama o Assembly Linker \(Al.exe, também conhecido como Alink\) para gerar um assembly com um manifesto.  O vinculador reportou um erro no estágio de pré\-emissão da criação do assembly.  
  
 Isso pode ocorrer se houver problemas com o arquivo de chave ou o contêiner de chave especificado.  Para marcar totalmente um assembly, é necessário fornecer um arquivo de chave válido que contenha informações sobre as chaves públicas e privadas.  Para marcar um atraso em um assembly, é necessário marcar a caixa de seleção **Somente sinal de atraso** e fornecer um arquivo de chave válido que contenha informações sobre as informações de chave pública.  A chave privada não é necessária quando um assembly estiver marcado com atraso.  Para obter mais informações, consulte [Como: assinar um Assembly \(Visual Studio\)](http://msdn.microsoft.com/pt-br/f468a7d3-234c-4353-924d-8e0ae5896564).  
  
 **Identificação do erro:** BC30140  
  
### Para corrigir este erro  
  
1.  Examine a mensagem de erro entre aspas e consulte o tópico [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/pt-br/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) para obter mais explicações e aconselhamento sobre o erro AL1019  
  
2.  Se o erro persistir, reúna informações sobre as circunstâncias e notifique o Microsoft Product Support Services.  
  
## Consulte também  
 [Como: assinar um Assembly \(Visual Studio\)](http://msdn.microsoft.com/pt-br/f468a7d3-234c-4353-924d-8e0ae5896564)   
 [Página de Assinatura, Designer de Projeto](/visual-studio/ide/reference/signing-page-project-designer)   
 [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)   
 [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/pt-br/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)   
 [Fale conosco](/visual-studio/ide/talk-to-us)