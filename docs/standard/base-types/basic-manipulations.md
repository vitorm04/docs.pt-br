---
title: 'Como: executar manipulações de cadeias de caracteres básicas no .NET'
description: Veja um exemplo que chama vários métodos de cadeia de caracteres.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET Framework], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
author: rpetrusha
ms.author: ronpet
ms.custom: seodec18
ms.openlocfilehash: 11f8043745c631a642b437339240cbf06fc8df5b
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130631"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a>Como: executar manipulações de cadeias de caracteres básicas no .NET
O exemplo a seguir usa alguns dos métodos discutidos nos tópicos de [Operações de cadeias de caracteres básicas](../../../docs/standard/base-types/basic-string-operations.md) para construir uma classe que realiza manipulações de cadeia de caracteres de uma maneira que pode ser encontrada em um aplicativo real. A classe `MailToData` armazena o nome e endereço de um indivíduo em propriedades separadas e fornece uma maneira de combinar os campos `City`, `State` e `Zip` em uma única cadeia de caracteres para exibição para o usuário. Além disso, a classe permite que o usuário insira as informações de cidade, estado e CEP como uma única cadeia de caracteres. O aplicativo automaticamente analisa a única cadeia de caracteres e insere as informações adequadas na propriedade correspondente.  
  
 Para simplificar, este exemplo usa um aplicativo de console com uma interface de linha de comando.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
 [!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
 Quando o código anterior é executado, é solicitado que o usuário insira seu nome e endereço. O aplicativo coloca as informações nas propriedades adequadas e exibe as informações de volta para o usuário, criando uma única cadeia de caracteres que exibe as informações de cidade, estado e CEP.  
  
## <a name="see-also"></a>Consulte também

- [Operações básicas de cadeias de caracteres](../../../docs/standard/base-types/basic-string-operations.md)
