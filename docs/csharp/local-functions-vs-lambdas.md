---
title: "Funções locais vs. expressões lambda"
description: "Por que as funções locais podem ser uma escolha melhor que as expressões lambda"
keywords: "C#, .NET, .NET Core, Últimos Recursos, Novidades, funções locais, expressões lambda"
author: BillWagner
ms.author: wiwagn
ms.date: 10/27/2016
ms.topic: article
ms.prod: visual-studio-dev-15
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 368d1752-3659-489a-97b4-f15d87e49ae3
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: bba2a8d183f928e298c452f6ec132f3eb9dffbd3
ms.lasthandoff: 03/13/2017

---

### <a name="local-functions-compared-to-lambda-expressions"></a>Funções locais comparadas com expressões lambda

Em alguns casos de uso, você pode criar uma expressão lambda e usá-la sem precisar criar uma função local. Eis um método assíncrono de exemplo que faz exatamente isso:

[!code-csharp[TaskLambdaExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Método de retorno de tarefa com uma expressão lambda")]

No entanto, há vários motivos para preferir usar funções locais em vez de definir e chamar expressões lambda.

Primeiro, para as expressões lambda, o compilador deve criar uma classe anônima e uma instância dessa classe para armazenar todas as variáveis capturadas pelo fechamento. O fechamento desta expressão lambda contém as variáveis `address`, `index` e `name`. 

Segundo, as expressões lambda são implementadas instanciando um delegado e invocando esse delegado. As funções locais são implementadas como chamadas de método.
A instanciação necessária para expressões lambda significa alocações de memória extra, o que podem ser um fator de desempenho em caminhos de código crítico de tempo.
As funções locais não incorrem nessa sobrecarga.

Terceiro, as funções locais podem ser chamadas antes de serem definidas. As expressões lambda devem ser declaradas antes de serem definidas. Isso significa que funções locais são mais fáceis de usar em algoritmos recursivos:

[!code-csharp[LocalFunctionFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Fatorial recursiva usando a função local")]

Compare essa implementação com uma versão que usa expressões lambda:

[!code-csharp[26_LambdaFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Fatorial recursiva usando expressões lambda")]

Observe que a versão usando a expressão lambda deve declarar e inicializar a expressão lambda, `nthFactorial` antes de defini-la. Não fazer isso resulta em um erro em tempo de compilação para referenciar `nthFactorial` antes de atribuí-lo.
Os algoritmos recursivos são mais fáceis de criar usando funções locais. 

Embora as funções locais possam parecer redundantes para expressões lambda, elas realmente têm finalidades e usos diferentes.
As funções locais são mais eficientes para quando você deseja escrever uma função que é chamada apenas do contexto de outro método.


