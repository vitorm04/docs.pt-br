---
title: Criar um grupo aninhado (LINQ em C#)
description: Saiba como criar um grupo aninhado em uma expressão de consulta LINQ em C#.
ms.date: 12/1/2016
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: c973048d0859f61596c62c294131b8c00d0039f8
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404743"
---
# <a name="create-a-nested-group"></a>Criar um grupo aninhado

O exemplo a seguir mostra como criar grupos aninhados em uma expressão de consulta LINQ. Cada grupo que é criado de acordo com o ano do aluno ou nível de ensino, é subdividido em grupos com base nos nomes das pessoas.

## <a name="example"></a>Exemplo

> [!NOTE]
> Este exemplo contém referências a objetos que são definidos no código de exemplo em [Consultar uma coleção de objetos](query-a-collection-of-objects.md).

[!code-csharp[csProgGuideLINQ#24](~/samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]

Observe que três loops `foreach` aninhados são necessários para iterar sobre os elementos internos de um grupo aninhado.

## <a name="see-also"></a>Consulte também

[LINQ (Consulta Integrada à Linguagem)](index.md)
