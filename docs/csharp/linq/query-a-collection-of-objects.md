---
title: "Consultar uma coleção de objetos"
description: "Como consultar coleções."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6694d28355b638c1fe55df0b44700f2dd8d839de
ms.lasthandoff: 03/13/2017

---
# <a name="query-a-collection-of-objects"></a>Consultar uma coleção de objetos
Este exemplo mostra como executar uma consulta simples em uma lista de objetos `Student`. Cada objeto `Student` contém algumas informações básicas sobre o aluno e uma lista que representa as pontuações do aluno em quatro provas.  
  
 Este aplicativo serve como a estrutura para muitos outros exemplos nesta seção que usam as mesmas fontes de dados `students`.  
  
## <a name="example"></a>Exemplo  
 A consulta a seguir retorna os alunos que receberam uma pontuação de 90 ou mais em sua primeira prova.  
  
 [!code-cs[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
 Essa consulta é intencionalmente simples para que você possa testar. Por exemplo, você pode testar mais condições na cláusula `where` ou usar uma clausula `orderby` para classificar os resultados.  
  

## <a name="see-also"></a>Consulte também  
 [Expressões de consulta LINQ](index.md)
