---
title: Especificar dinamicamente filtros predicados em tempo de execução (LINQ em C#)
description: Saiba como especificar dinamicamente filtros predicados em tempo de execução usando o LINQ em C#.
ms.date: 12/1/2016
ms.assetid: 90238470-0767-497c-916c-52d0d16845e0
ms.openlocfilehash: ece5940edd615f30acab06a429de300e27811a66
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52296068"
---
# <a name="dynamically-specify-predicate-filters-at-runtime"></a>Especificar filtros predicados dinamicamente em tempo de execução

Em alguns casos, você não sabe até o tempo de execução quantos predicados precisa aplicar aos elementos de origem na cláusula `where`. Uma maneira de especificar dinamicamente vários filtros de predicados é usar o método <xref:System.Linq.Enumerable.Contains%2A>, conforme mostrado no exemplo a seguir. O exemplo é construído de duas maneiras. Primeiro, o projeto é executado filtrando valores que são fornecidos no programa. Em seguida, o projeto é executado novamente usando a entrada fornecida em tempo de execução.

## <a name="to-filter-by-using-the-contains-method"></a>Para filtrar usando o método Contains

1. Abra um novo aplicativo de console e nomeie-o como `PredicateFilters`.

2. Copie a classe `StudentClass` de [Consultar uma coleção de objetos](query-a-collection-of-objects.md) e cole-a no namespace `PredicateFilters` sob a classe `Program`. `StudentClass` fornece uma lista de objetos `Student`.

3. Comente o método `Main` em `StudentClass`.

4. Substitua a classe `Program` pelo código a seguir:

     [!code-csharp[csProgGuideLINQ#26](~/samples/snippets/csharp/concepts/linq/how-to-dynamically-specify-predicate-filters-at-runtime_1.cs)]

5. Adicione a seguinte linha ao método `Main` na classe `DynamicPredicates`, sob a declaração de `ids`.

     ```csharp
     QueryById(ids);
     ```

6. Execute o projeto.

7. A saída a seguir é exibida em uma janela do console:

     Garcia: 114

     O'Donnell: 112

     Omelchenko: 111

8. A próxima etapa é executar o projeto novamente, desta vez usando a entrada inserida em tempo de execução em vez da matriz `ids`. Altere `QueryByID(ids)` para `QueryByID(args)` no método `Main`.

9. Execute o projeto com os argumentos de linha de comando `122 117 120 115`. Quando o projeto é executado, esses valores se tornam elementos de `args`, o parâmetro do método `Main`.

10. A saída a seguir é exibida em uma janela do console:

     Adams: 120

     Feng: 117

     Garcia: 115

     Tucker: 122

## <a name="to-filter-by-using-a-switch-statement"></a>Para filtrar usando uma instrução switch

1. Você pode usar uma instrução `switch` para selecionar entre consultas alternativas predeterminadas. No exemplo a seguir, `studentQuery` usa uma cláusula `where` diferente dependendo de qual nível de ensino ou ano, é especificado em tempo de execução.

2. Copie o método a seguir e cole-o na classe `DynamicPredicates`.

     [!code-csharp[csProgGuideLINQ#27](~/samples/snippets/csharp/concepts/linq//how-to-dynamically-specify-predicate-filters-at-runtime_2.cs)]

3. No método `Main`, substitua a chamada para `QueryByID` pela chamada a seguir, que envia o primeiro elemento da matriz `args` como seu argumento: `QueryByYear(args[0])`.

4. Execute o projeto com um argumento de linha de comando de um valor inteiro entre 1 e 4.

## <a name="see-also"></a>Consulte também

- [LINQ (Consulta Integrada à Linguagem)](index.md)
- [Cláusula where](../language-reference/keywords/where-clause.md)
