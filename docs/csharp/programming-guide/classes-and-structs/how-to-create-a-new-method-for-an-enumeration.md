---
title: "Como criar um novo m&#233;todo para uma enumera&#231;&#227;o (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "extensibilidade enum [C#]"
  - "enumerações [C#]"
  - "métodos de extensão [C#], para enumerações"
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como criar um novo m&#233;todo para uma enumera&#231;&#227;o (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Você pode usar os métodos de extensão para adicionar funcionalidade específica a um tipo específico de enum.  
  
## Exemplo  
 No exemplo a seguir, o `Grades` enumeração representa as letras possíveis que um aluno pode ser exibida em uma classe.  Um método de extensão chamado `Passing` é adicionado para o `Grades` digite de forma que cada instância desse tipo agora "sabe" se ele representa uma passagem de nota ou não.  
  
 [!code-cs[csProgGuideExtensionMethods#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-create-a-new-method-for-an-enumeration_1.cs)]  
  
 Observe que o `Extensions` classe também contém uma variável estática que é atualizada dinamicamente e que o valor de retorno do método de extensão reflete o valor atual dessa variável.  Isso demonstra que, nos bastidores, os métodos de extensão são chamados diretamente na classe estática em que eles são definidos.  
  
## Compilando o código  
 Para executar esse código, copie e cole\-o em um Visual C\# projeto de aplicativo console que tenha sido criado em [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)].  Por padrão, esse projeto destina\-se a versão 3.5 da [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)], e ele tem uma referência a System.Core.dll e um `using` diretriz para System. LINQ.  Se um ou mais desses requisitos estão ausentes do projeto, você pode adicioná\-los manualmente.  Para obter mais informações, consulte [Como criar um projeto LINQ](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md).  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Métodos de extensão](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)