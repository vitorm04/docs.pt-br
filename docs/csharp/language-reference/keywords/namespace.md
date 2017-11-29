---
title: "namespace (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 76cc1adc21f6cfadc93da58250336705e43e333a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="namespace-c-reference"></a>namespace (Referência de C#)
A palavra-chave `namespace` é usada para declarar um escopo que contém um conjunto de objetos relacionados. Você pode usar um namespace para organizar elementos de código e criar tipos globalmente exclusivos.  
  
 [!code-csharp[csrefKeywordsNamespace#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_1.cs)]  
  
## <a name="remarks"></a>Comentários  
 Dentro de um namespace, você pode declarar um ou mais dos seguintes tipos:  
  
-   outro namespace  
  
-   [class](../../../csharp/language-reference/keywords/class.md)  
  
-   [interface](../../../csharp/language-reference/keywords/interface.md)  
  
-   [struct](../../../csharp/language-reference/keywords/struct.md)  
  
-   [enum](../../../csharp/language-reference/keywords/enum.md)  
  
-   [delegate](../../../csharp/language-reference/keywords/delegate.md)  
  
 Quer você declare explicitamente ou não um namespace em um arquivo de origem C#, o compilador adiciona um namespace padrão. Este namespace sem nome, às vezes chamado de namespace global, está presente em todos os arquivos. Qualquer identificador no namespace global está disponível para uso em um namespace nomeado.  
  
 Os namespaces implicitamente têm acesso público e não isso é modificável. Para uma discussão sobre os modificadores de acesso que você pode atribuir a elementos em um namespace, consulte [Modificadores de acesso](../../../csharp/language-reference/keywords/access-modifiers.md).  
  
 É possível definir um namespace em duas ou mais declarações. Por exemplo, o exemplo a seguir define duas classes como parte do namespace `MyCompany`:  
  
 [!code-csharp[csrefKeywordsNamespace#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_2.cs)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como chamar um método estático em um namespace aninhado.  
  
 [!code-csharp[csrefKeywordsNamespace#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_3.cs)]  
  
## <a name="for-more-information"></a>Para obter mais informações  
 Para obter mais informações sobre o uso de namespaces, consulte os seguintes tópicos:  
  
-   [Namespaces](../../../csharp/programming-guide/namespaces/index.md)  
  
-   [Usando namespaces](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [Como usar o alias de namespace global](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
 [Palavras-chave de namespace](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [using](../../../csharp/language-reference/keywords/using.md)
