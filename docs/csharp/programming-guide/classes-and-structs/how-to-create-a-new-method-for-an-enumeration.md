---
title: Como criar um novo método para um guia de C# programação de enumeração
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 0d8e562342239c8ac3c53e05086ede9c234d0b63
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705646"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a>Como criar um novo método para uma enumeração (C# guia de programação)
Você pode usar métodos de extensão para adicionar funcionalidades específica para um tipo de enumeração específico.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, a enumeração `Grades` representa as letras possíveis que um aluno pode receber em uma classe. Um método de extensão chamado `Passing` é adicionado ao tipo `Grades` de forma que cada instância desse tipo agora "sabe" se ele representa uma nota de aprovação ou não.  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 Observe que a classe `Extensions` também contém uma variável estática atualizada dinamicamente e que o valor retornado do método de extensão reflete o valor atual dessa variável. Isso demonstra que, nos bastidores, os métodos de extensão são chamados diretamente na classe estática na qual eles são definidos.  
  
## <a name="see-also"></a>Veja também

- [Guia de Programação em C#](../index.md)
- [Métodos de Extensão](./extension-methods.md)
