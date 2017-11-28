---
title: "Como: Store e consultas reutilização"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a012bd79-1809-45e3-adea-0229532396cc
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 321be8e2cd38ea1138e54587ee876ceb82f67440
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-store-and-reuse-queries"></a>Como: Store e consultas reutilização
Quando você tiver um aplicativo que executa consultas estrutural semelhantes muitas vezes, você geralmente pode aumentar o desempenho criando a consulta uma hora e executando a várias vezes com parâmetros diferentes. Por exemplo, um aplicativo pode precisar recuperar todos os clientes que estão em uma cidade específica, onde cidade é especificada em tempo de execução pelo usuário em um formulário. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]oferece suporte ao uso de *compilado consultas* para essa finalidade.  
  
> [!NOTE]
>  Esse padrão de uso representa o uso mais comum para consultas compilados. Outras abordagens são possíveis. Por exemplo, consultas compiladas podem ser armazenadas como membros estáticos em uma classe parcial que estende o código gerado pelo designer.  
  
## <a name="example"></a>Exemplo  
 Em muitos cenários talvez queira reutilizar as consultas através dos limites de segmento. Nesses casos, armazenar as consultas compilados em variáveis estáticas é muito eficiente. O exemplo de código a seguir pressupõe uma classe de `Queries` projetada para armazenar consultas compilados, e pressupõe uma classe Northwind que representa <xref:System.Data.Linq.DataContext>fortemente tipado.  
  
 [!code-csharp[DLinqQuerying#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#6)]
 [!code-vb[DLinqQuerying#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#6)]  
  
 [!code-csharp[DLinqQuerying#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#7)]
 [!code-vb[DLinqQuerying#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#7)]  
  
## <a name="example"></a>Exemplo  
 Não é possível no momento consultas de armazenamento (em variáveis estáticas) que retornam um *tipo anônimo*, porque o tipo não tem um nome para fornecer como um argumento genérico. O exemplo a seguir mostra como você pode contornar do problema criando um tipo que pode representar o resultado, e o usar como um argumento genérico.  
  
 [!code-csharp[DLinqQuerying#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#8)]
 [!code-vb[DLinqQuerying#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#8)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Data.Linq.CompiledQuery>  
 [Conceitos de consulta](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [Consultando o banco de dados](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
