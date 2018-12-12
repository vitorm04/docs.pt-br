---
title: Namespaces – Guia de Programação em C#
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 4abdf8a0008ce50a89eb5f3ad3512a9579dc832a
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236746"
---
# <a name="namespaces-c-programming-guide"></a>Namespaces (Guia de Programação em C#)

Os namespaces são usados intensamente em programações de C# de duas maneiras. Em primeiro lugar, o .NET Framework usa namespaces para organizar suas muitas classes, da seguinte maneira:  
  
[!code-csharp[csProgGuide#22](../inside-a-program/codesnippet/CSharp/index_1.cs)]  
  
`System` é um namespace e `Console` é uma classe nesse namespace. A palavra-chave `using` pode ser usada para que o nome completo não seja necessário, como no exemplo a seguir:  
  
[!code-csharp[csProgGuide#1](../inside-a-program/codesnippet/CSharp/index_2.cs)]  
  
[!code-csharp[csProgGuide#25](../inside-a-program/codesnippet/CSharp/index_3.cs)]  
  
Para saber mais, confira [Diretiva using](../../language-reference/keywords/using-directive.md).  
  
Em segundo lugar, declarar seus próprios namespaces pode ajudar a controlar o escopo dos nomes de classe e de método em projetos de programação maiores. Use a palavra-chave [namespace](../../language-reference/keywords/namespace.md) para declarar um namespace, como no exemplo a seguir:  
  
[!code-csharp[csProgGuideNamespaces#6](codesnippet/CSharp/index_4.cs)]

O nome do namespace deve ser um [nome do identificador](../inside-a-program/identifier-names.md) válido em C#.

## <a name="namespaces-overview"></a>Visão geral sobre namespaces  

Os namespaces têm as seguintes propriedades:  
  
- Eles organizam projetos de códigos grandes.  
- Eles são delimitados usando o operador `.`.  
- A diretiva `using` elimina a necessidade de especificar o nome do namespace para cada classe.  
- O namespace `global` é o namespace "raiz": `global::System` sempre fará referência ao namespace do .NET <xref:System>.  

## <a name="c-language-specification"></a>Especificação da Linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Usando namespaces](using-namespaces.md)
- [Como: usar o alias de namespace global](how-to-use-the-global-namespace-alias.md)
- [Como: usar o My Namespace](how-to-use-the-my-namespace.md)
- [Guia de Programação em C#](../index.md)  
- [Nomes de identificadores](../inside-a-program/identifier-names.md)
- [Palavras-chave de namespace](../../language-reference/keywords/namespace-keywords.md)  
- [Diretiva using](../../language-reference/keywords/using-directive.md)  
- [:: ??](../../language-reference/operators/namespace-alias-qualifer.md)  
- [. ??](../../language-reference/operators/member-access-operator.md)
