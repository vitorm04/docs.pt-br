---
title: Manipulações básicas de cadeia de caracteres no .NET
description: Veja um exemplo que chama vários métodos de cadeia de caracteres.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
ms.openlocfilehash: cc04f0c874b732668b4813f8325bd7060927f22a
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92889121"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a>Como: executar manipulações de cadeias de caracteres básicas no .NET

O exemplo a seguir usa alguns dos métodos discutidos nos tópicos de [Operações de cadeias de caracteres básicas](basic-string-operations.md) para construir uma classe que realiza manipulações de cadeia de caracteres de uma maneira que pode ser encontrada em um aplicativo real. A classe `MailToData` armazena o nome e endereço de um indivíduo em propriedades separadas e fornece uma maneira de combinar os campos `City`, `State` e `Zip` em uma única cadeia de caracteres para exibição para o usuário. Além disso, a classe permite que o usuário insira as informações de cidade, estado e CEP como uma única cadeia de caracteres. O aplicativo automaticamente analisa a única cadeia de caracteres e insere as informações adequadas na propriedade correspondente.  
  
Para simplificar, este exemplo usa um aplicativo de console com uma interface de linha de comando.  
  
## <a name="example"></a>Exemplo  

[!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
[!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
Quando o código anterior é executado, o usuário é solicitado a inserir seu nome e endereço. O aplicativo coloca as informações nas propriedades adequadas e exibe as informações de volta para o usuário, criando uma única cadeia de caracteres que exibe as informações de cidade, estado e CEP.  
  
## <a name="see-also"></a>Veja também

- [Operações básicas de cadeia de caracteres](basic-string-operations.md)
