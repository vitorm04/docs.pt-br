---
title: Criar um grupo aninhado
description: Como criar um grupo aninhado.
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: 232aa46d975d7c338bbc776e3867f2e566601fde
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="create-a-nested-group"></a>Criar um grupo aninhado

O exemplo a seguir mostra como criar grupos aninhados em uma expressão de consulta LINQ. Cada grupo que é criado de acordo com o ano do aluno ou nível de ensino, é subdividido em grupos com base nos nomes das pessoas.  
  
## <a name="example"></a>Exemplo

 > [!NOTE]
 > Este exemplo contém referências a objetos que são definidos no código de exemplo em [Consultar uma coleção de objetos](query-a-collection-of-objects.md). 

 [!code-csharp[csProgGuideLINQ#24](../../../samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]  
  
 Observe que três loops `foreach` aninhados são necessários para iterar sobre os elementos internos de um grupo aninhado.  
  
## <a name="see-also"></a>Consulte também  
 [Expressões de consulta LINQ](index.md)
