---
title: Criar um grupo aninhado
description: Como criar um grupo aninhado.
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 361ac1f224c6eef292fcf8434c7e465c9448b19c
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="create-a-nested-group"></a>Criar um grupo aninhado

O exemplo a seguir mostra como criar grupos aninhados em uma expressão de consulta LINQ. Cada grupo que é criado de acordo com o ano do aluno ou nível de ensino, é subdividido em grupos com base nos nomes das pessoas.  
  
## <a name="example"></a>Exemplo

 > [!NOTE]
 > Este exemplo contém referências a objetos que são definidos no código de exemplo em [Consultar uma coleção de objetos](query-a-collection-of-objects.md). 

 [!code-cs[csProgGuideLINQ#24](../../../samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]  
  
 Observe que três loops `foreach` aninhados são necessários para iterar sobre os elementos internos de um grupo aninhado.  
  
## <a name="see-also"></a>Consulte também  
 [Expressões de consulta LINQ](index.md)

