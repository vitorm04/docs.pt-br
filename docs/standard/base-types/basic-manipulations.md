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
ms.openlocfilehash: 659f01cc1d7ae03e12e83329e4fd2446b7512475
ms.sourcegitcommit: ffd4d5e824db6c5f0c3521c0e802fd9e8f0edcbe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/04/2020
ms.locfileid: "93342612"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a><span data-ttu-id="25fcf-103">Como: executar manipulações de cadeias de caracteres básicas no .NET</span><span class="sxs-lookup"><span data-stu-id="25fcf-103">How to: Perform Basic String Manipulations in .NET</span></span>

<span data-ttu-id="25fcf-104">O exemplo a seguir usa alguns dos métodos discutidos nos tópicos de [Operações de cadeias de caracteres básicas](basic-string-operations.md) para construir uma classe que realiza manipulações de cadeia de caracteres de uma maneira que pode ser encontrada em um aplicativo real.</span><span class="sxs-lookup"><span data-stu-id="25fcf-104">The following example uses some of the methods discussed in the [Basic String Operations](basic-string-operations.md) topics to construct a class that performs string manipulations in a manner that might be found in a real-world application.</span></span> <span data-ttu-id="25fcf-105">A classe `MailToData` armazena o nome e endereço de um indivíduo em propriedades separadas e fornece uma maneira de combinar os campos `City`, `State` e `Zip` em uma única cadeia de caracteres para exibição para o usuário.</span><span class="sxs-lookup"><span data-stu-id="25fcf-105">The `MailToData` class stores the name and address of an individual in separate properties and provides a way to combine the `City`, `State`, and `Zip` fields into a single string for display to the user.</span></span> <span data-ttu-id="25fcf-106">Além disso, a classe permite que o usuário insira a cidade, o estado e as informações de CEP como uma única cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="25fcf-106">Furthermore, the class allows the user to enter the city, state, and zip code information as a single string.</span></span> <span data-ttu-id="25fcf-107">O aplicativo analisa automaticamente a única cadeia de caracteres e insere as informações apropriadas na propriedade correspondente.</span><span class="sxs-lookup"><span data-stu-id="25fcf-107">The application automatically parses the single string and enters the proper information into the corresponding property.</span></span>

<span data-ttu-id="25fcf-108">Para simplificar, este exemplo usa um aplicativo de console com uma interface de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="25fcf-108">For simplicity, this example uses a console application with a command-line interface.</span></span>

## <a name="example"></a><span data-ttu-id="25fcf-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="25fcf-109">Example</span></span>

[!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
[!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]

<span data-ttu-id="25fcf-110">Quando o código anterior é executado, o usuário é solicitado a inserir seu nome e endereço.</span><span class="sxs-lookup"><span data-stu-id="25fcf-110">When the preceding code is executed, the user is asked to enter their name and address.</span></span> <span data-ttu-id="25fcf-111">O aplicativo coloca as informações nas propriedades apropriadas e exibe as informações de volta para o usuário, criando uma única cadeia de caracteres que exibe a cidade, o estado e as informações de CEP.</span><span class="sxs-lookup"><span data-stu-id="25fcf-111">The application places the information in the appropriate properties and displays the information back to the user, creating a single string that displays the city, state, and zip code information.</span></span>

## <a name="see-also"></a><span data-ttu-id="25fcf-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="25fcf-112">See also</span></span>

- [<span data-ttu-id="25fcf-113">Operações básicas de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="25fcf-113">Basic String Operations</span></span>](basic-string-operations.md)
