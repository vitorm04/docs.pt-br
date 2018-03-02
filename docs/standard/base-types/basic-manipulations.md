---
title: "Como executar manipulações de cadeias de caracteres básicas no .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET Framework], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8d3d5351a0a639a3f0b674640bcaaf7321ca0d76
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a><span data-ttu-id="8e3d5-102">Como: executar manipulações de cadeias de caracteres básicas no .NET</span><span class="sxs-lookup"><span data-stu-id="8e3d5-102">How to: Perform Basic String Manipulations in .NET</span></span>
<span data-ttu-id="8e3d5-103">O exemplo a seguir usa alguns dos métodos discutidos nos tópicos de [Operações de cadeias de caracteres básicas](../../../docs/standard/base-types/basic-string-operations.md) para construir uma classe que realiza manipulações de cadeia de caracteres de uma maneira que pode ser encontrada em um aplicativo real.</span><span class="sxs-lookup"><span data-stu-id="8e3d5-103">The following example uses some of the methods discussed in the [Basic String Operations](../../../docs/standard/base-types/basic-string-operations.md) topics to construct a class that performs string manipulations in a manner that might be found in a real-world application.</span></span> <span data-ttu-id="8e3d5-104">A classe `MailToData` armazena o nome e endereço de um indivíduo em propriedades separadas e fornece uma maneira de combinar os campos `City`, `State` e `Zip` em uma única cadeia de caracteres para exibição para o usuário.</span><span class="sxs-lookup"><span data-stu-id="8e3d5-104">The `MailToData` class stores the name and address of an individual in separate properties and provides a way to combine the `City`, `State`, and `Zip` fields into a single string for display to the user.</span></span> <span data-ttu-id="8e3d5-105">Além disso, a classe permite que o usuário insira as informações de cidade, estado e CEP como uma única cadeia de caracteres. O aplicativo automaticamente analisa a única cadeia de caracteres e insere as informações adequadas na propriedade correspondente.</span><span class="sxs-lookup"><span data-stu-id="8e3d5-105">Furthermore, the class allows the user to enter the city, state, and ZIP Code information as a single string; the application automatically parses the single string and enters the proper information into the corresponding property.</span></span>  
  
 <span data-ttu-id="8e3d5-106">Para simplificar, este exemplo usa um aplicativo de console com uma interface de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="8e3d5-106">For simplicity, this example uses a console application with a command-line interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e3d5-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8e3d5-107">Example</span></span>  
 [!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
 [!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
 <span data-ttu-id="8e3d5-108">Quando o código anterior é executado, é solicitado que o usuário insira seu nome e endereço.</span><span class="sxs-lookup"><span data-stu-id="8e3d5-108">When the preceding code is executed, the user is asked to enter his or her name and address.</span></span> <span data-ttu-id="8e3d5-109">O aplicativo coloca as informações nas propriedades adequadas e exibe as informações de volta para o usuário, criando uma única cadeia de caracteres que exibe as informações de cidade, estado e CEP.</span><span class="sxs-lookup"><span data-stu-id="8e3d5-109">The application places the information in the appropriate properties and displays the information back to the user, creating a single string that displays the city, state, and ZIP Code information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e3d5-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e3d5-110">See Also</span></span>  
 [<span data-ttu-id="8e3d5-111">Operações básicas de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="8e3d5-111">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
