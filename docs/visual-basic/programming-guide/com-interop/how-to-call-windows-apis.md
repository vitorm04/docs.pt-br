---
title: "Como chamar APIs do Windows (Visual Basic) | Microsoft Docs"
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
  - "Chamadas à API"
  - "Chamadas à API, invocação de plataforma"
  - "chamadas, procedimentos armazenados"
  - "API do Windows, Chamando "
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como chamar APIs do Windows (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Este exemplo define e chama a função `MessageBox` na user32.dll e, em seguida, passa uma cadeia de caracteres para ela.  
  
## Exemplo  
 [!CODE [VbVbalrInterop#1](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrInterop#1)]  
  
## Compilando o código  
 Este exemplo requer:  
  
-   Uma referência ao namespace <xref:System>.  
  
## Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   O método não é estático, é abstrato ou foi definido anteriormente.  O tipo pai é uma interface, ou o comprimento do *Name* ou *dllName* é zero.  \(<xref:System.ArgumentException>\)  
  
-   O *Name* ou *dllName* é `Nothing`.  \(<xref:System.ArgumentNullException>\)  
  
-   O tipo recipiente foi criado anteriormente usando `CreateType`.  \(<xref:System.InvalidOperationException>\)  
  
## Consulte também  
 [A Closer Look at Platform Invoke](http://msdn.microsoft.com/pt-br/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)   
 [Exemplos de invocação de plataforma](../Topic/Platform%20Invoke%20Examples.md)   
 [Consumindo funções de DLL não gerenciadas](../Topic/Consuming%20Unmanaged%20DLL%20Functions.md)   
 [Defining a Method with Reflection Emit](http://msdn.microsoft.com/pt-br/84fd3bf6-628f-41aa-83d9-b990cf926e81)   
 [Instruções passo a passo: chamando APIs do Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)   
 [Interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/index.md)