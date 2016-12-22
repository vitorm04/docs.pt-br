---
title: "Como modificar o conte&#250;do de uma cadeia de caracteres (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "cadeias de caracteres [C#], modificando"
ms.assetid: b6c20bba-ce22-43d7-ad1b-5ce65f714055
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como modificar o conte&#250;do de uma cadeia de caracteres (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Como seqüências de caracteres são  *imutáveis*, não é possível \(sem usar código não seguro\) para modificar o valor de um objeto de seqüência de caracteres após ele ter sido criado.  No entanto, existem muitas maneiras de modificar o valor de uma seqüência de caracteres e armazenar o resultado em um novo objeto de seqüência de caracteres.  O <xref:System.String?displayProperty=fullName> classe fornece métodos que operam em uma entrada em seqüência e retornam um novo objeto de seqüência de caracteres.  Em muitos casos, você pode atribuir o novo objeto à variável que mantinha a seqüência de caracteres original.  O <xref:System.Text.RegularExpressions.Regex?displayProperty=fullName> classe fornece métodos adicionais que funcionam de maneira semelhante.  O <xref:System.Text.StringBuilder?displayProperty=fullName> classe fornece um buffer de caractere que você pode modificar "no local." Você pode chamar o <xref:System.Text.StringBuilder.ToString%2A?displayProperty=fullName> método para criar um novo objeto de seqüência de caracteres que contém o conteúdo atual do buffer.  
  
## Exemplo  
 O exemplo a seguir mostra várias maneiras para substituir ou remover substrings em uma seqüência de caracteres especificada.  
  
 [!code-cs[csProgGuideStrings#28](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_1.cs)]  
  
## Exemplo  
 Para acessar os caracteres individuais em uma seqüência de caracteres usando a notação de matriz, você pode usar o <xref:System.Text.StringBuilder> objeto, o que sobrecarrega o `[]` operador para fornecer acesso a seu buffer interno de caractere.  Você também pode converter a seqüência de caracteres em uma matriz de caracteres usando o <xref:System.String.ToCharArray%2A> método.  O exemplo a seguir usa `ToCharArray` para criar a matriz.  Alguns elementos dessa matriz, em seguida, são modificados.  Um construtor de seqüência de caracteres que leva uma matriz de char como parâmetro de entrada, em seguida, é chamada para criar uma nova seqüência.  
  
 [!code-cs[csProgGuideStrings#24](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_2.cs)]  
  
## Exemplo  
 O exemplo a seguir é fornecido para essas situações raras em que você deseja modificar um seqüência de caracteres no local, usando o código não seguro de maneira semelhante para matrizes de caracteres de estilo C.  O exemplo mostra como acessar os caracteres individuais "in\-loco" usando a palavra\-chave fixed.  Ele também demonstra um possível efeito colateral operações não seguras em seqüências de caracteres que resulta da forma em que o compilador C\# armazena internamente cadeias de caracteres \(estagiários\).  Em geral, você não deve usar essa técnica, a menos que seja absolutamente necessário.  
  
 [!code-cs[csProgGuideStrings#29](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_3.cs)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Cadeias de caracteres](../../../csharp/programming-guide/strings/index.md)