---
title: 'Como: exibir o SQL gerado'
description: Saiba como exibir o código SQL gerado para consultas usando a propriedade log para ajudar a entender LINQ to SQL funcionalidade e para depuração.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 626492c0-5ee3-4675-88e8-8c40379510b6
ms.openlocfilehash: 81f6b9603cc7f8b7863f787272ce6a1af920fa75
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169473"
---
# <a name="how-to-display-generated-sql"></a><span data-ttu-id="6c3cc-103">Como: exibir o SQL gerado</span><span class="sxs-lookup"><span data-stu-id="6c3cc-103">How to: Display Generated SQL</span></span>

<span data-ttu-id="6c3cc-104">Você pode exibir o código SQL gerado para consultas e processamento de alteração usando a propriedade de <xref:System.Data.Linq.DataContext.Log%2A> .</span><span class="sxs-lookup"><span data-stu-id="6c3cc-104">You can view the SQL code generated for queries and change processing by using the <xref:System.Data.Linq.DataContext.Log%2A> property.</span></span> <span data-ttu-id="6c3cc-105">Essa abordagem pode ser útil para entender a funcionalidade de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] e depure questões específicas.</span><span class="sxs-lookup"><span data-stu-id="6c3cc-105">This approach can be useful for understanding [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] functionality and for debugging specific problems.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c3cc-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6c3cc-106">Example</span></span>  

 <span data-ttu-id="6c3cc-107">O exemplo a seguir usa a propriedade de <xref:System.Data.Linq.DataContext.Log%2A> para exibir o código SQL na janela do console antes que o código seja executado.</span><span class="sxs-lookup"><span data-stu-id="6c3cc-107">The following example uses the <xref:System.Data.Linq.DataContext.Log%2A> property to display SQL code in the console window before the code is executed.</span></span>  <span data-ttu-id="6c3cc-108">Você pode usar essa propriedade com consulta, inserir, atualizar, excluir e comandos.</span><span class="sxs-lookup"><span data-stu-id="6c3cc-108">You can use this property with query, insert, update, and delete commands.</span></span>  
  
 <span data-ttu-id="6c3cc-109">As linhas da janela do console são as que você vê ao executar o código de Visual Basic ou C# a seguir.</span><span class="sxs-lookup"><span data-stu-id="6c3cc-109">The lines from the console window are what you see when you execute the Visual Basic or C# code that follows.</span></span>  
  
```console  
SELECT [t0].[CustomerID], [t0].[CompanyName], [t0].[ContactName], [t0].[ContactT  
itle], [t0].[Address], [t0].[City], [t0].[Region], [t0].[PostalCode], [t0].[Coun  
try], [t0].[Phone], [t0].[Fax]  
FROM [dbo].[Customers] AS [t0]  
WHERE [t0].[City] = @p0  
-- @p0: Input String (Size = 6; Prec = 0; Scale = 0) [London]  
-- Context: SqlProvider(Sql2005) Model: AttributedMetaModel Build: 3.5.20810.0  
```  
  
```console  
AROUT  
BSBEV  
CONSH  
EASTC  
NORTS  
SEVES  
```  
  
 [!code-csharp[DLinqDebuggingSupport#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#1)]
 [!code-vb[DLinqDebuggingSupport#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6c3cc-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="6c3cc-110">See also</span></span>

- [<span data-ttu-id="6c3cc-111">Depuração de suporte</span><span class="sxs-lookup"><span data-stu-id="6c3cc-111">Debugging Support</span></span>](debugging-support.md)
