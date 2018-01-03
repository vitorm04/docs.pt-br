---
title: 'Como: Exibir o SQL gerado'
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
ms.assetid: 626492c0-5ee3-4675-88e8-8c40379510b6
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 8ee5af338b0cbb979e923ba17f69bca2c6c64bc2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-generated-sql"></a>Como: Exibir o SQL gerado
Você pode exibir o código SQL gerado para consultas e processamento de alteração usando a propriedade de <xref:System.Data.Linq.DataContext.Log%2A> . Essa abordagem pode ser útil para entender a funcionalidade de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] e depure questões específicas.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa a propriedade de <xref:System.Data.Linq.DataContext.Log%2A> para exibir o código SQL na janela do console antes que o código seja executado.  Você pode usar essa propriedade com consulta, inserir, atualizar, excluir e comandos.  
  
 As linhas da janela do console são o que você vê quando você executa [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ou código em c que segue.  
  
```  
SELECT [t0].[CustomerID], [t0].[CompanyName], [t0].[ContactName], [t0].[ContactT  
itle], [t0].[Address], [t0].[City], [t0].[Region], [t0].[PostalCode], [t0].[Coun  
try], [t0].[Phone], [t0].[Fax]  
FROM [dbo].[Customers] AS [t0]  
WHERE [t0].[City] = @p0  
-- @p0: Input String (Size = 6; Prec = 0; Scale = 0) [London]  
-- Context: SqlProvider(Sql2005) Model: AttributedMetaModel Build: 3.5.20810.0  
```  
  
```  
AROUT  
BSBEV  
CONSH  
EASTC  
NORTS  
SEVES  
```  
  
 [!code-csharp[DLinqDebuggingSupport#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#1)]
 [!code-vb[DLinqDebuggingSupport#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Suporte à depuração](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)
