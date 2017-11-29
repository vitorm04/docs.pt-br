---
title: "Namespaces (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
caps.latest.revision: "27"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3eb645f5beb61d3cec97a70a54e660c65be52091
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="namespaces-c-programming-guide"></a>Namespaces (Guia de Programação em C#)
Os namespaces são usados intensamente em programações de C# de duas maneiras. Em primeiro lugar, o .NET Framework usa namespaces para organizar suas muitas classes, da seguinte maneira:  
  
 [!code-csharp[csProgGuide#22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_1.cs)]  
  
 `System` é um namespace e `Console` é uma classe nesse namespace. A palavra-chave `using` pode ser usada para que o nome completo não seja necessário, como no exemplo a seguir:  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_2.cs)]  
  
 [!code-csharp[csProgGuide#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_3.cs)]  
  
 Consulte [Diretiva using](../../../csharp/language-reference/keywords/using-directive.md) para obter mais informações.  
  
 Em segundo lugar, declarar seus próprios namespaces pode ajudar a controlar o escopo dos nomes de classe e de método em projetos de programação maiores. Use a palavra-chave [namespace](../../../csharp/language-reference/keywords/namespace.md) para declarar um namespace, como no exemplo a seguir:  
  
 [!code-csharp[csProgGuideNamespaces#6](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/index_4.cs)]  
  
## <a name="namespaces-overview"></a>Visão geral sobre namespaces  
 Os namespaces têm as seguintes propriedades:  
  
-   Eles organizam projetos de códigos grandes.  
  
-   Eles são delimitados usando o operador `.`.  
  
-   O `using directive` elimina a necessidade de especificar o nome do namespace para cada classe.  
  
-   O namespace `global` é o namespace "raiz": `global::System` sempre fará referência ao namespace do .NET Framework `System`.  
  
## <a name="related-sections"></a>Seções relacionadas  
 Consulte os tópicos a seguir para obter mais informações sobre namespaces:  
  
-   [Usando namespaces](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [Como usar o alias de namespace global](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
-   [Como usar o My Namespace](../../../csharp/programming-guide/namespaces/how-to-use-the-my-namespace.md)  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Palavras-chave de namespace](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [Diretiva using](../../../csharp/language-reference/keywords/using-directive.md)  
 [Operador ::](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [. ??](../../../csharp/language-reference/operators/member-access-operator.md)
