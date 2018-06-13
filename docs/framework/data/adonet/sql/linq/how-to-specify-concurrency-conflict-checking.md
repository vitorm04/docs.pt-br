---
title: 'Como: Especificar verificação de Simultaneidade- conflito'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2547fcb-58eb-4377-9948-1b8d76a0f3d7
ms.openlocfilehash: c7e4297f90174255f5df1e2a8b0b100b168abb08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362586"
---
# <a name="how-to-specify-concurrency-conflict-checking"></a><span data-ttu-id="3e6d4-102">Como: Especificar verificação de Simultaneidade- conflito</span><span class="sxs-lookup"><span data-stu-id="3e6d4-102">How to: Specify Concurrency-Conflict Checking</span></span>
<span data-ttu-id="3e6d4-103">Você pode especificar quais colunas de base de dados devem ser marcadas para ver se houver conflitos de simultaneidade quando você chama <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span><span class="sxs-lookup"><span data-stu-id="3e6d4-103">You can specify which columns of the database are to be checked for concurrency conflicts when you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span> <span data-ttu-id="3e6d4-104">Para obter mais informações, consulte [como: especificar quais membros são testados para conflitos de simultaneidade](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="3e6d4-104">For more information, see [How to: Specify Which Members are Tested for Concurrency Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e6d4-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3e6d4-105">Example</span></span>  
 <span data-ttu-id="3e6d4-106">O código a seguir especifica que o membro de `HomePage` nunca deve ser testado durante verificações de atualização.</span><span class="sxs-lookup"><span data-stu-id="3e6d4-106">The following code specifies that the `HomePage` member should never be tested during update checks.</span></span> <span data-ttu-id="3e6d4-107">Para obter mais informações, consulte <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="3e6d4-107">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3e6d4-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e6d4-108">See Also</span></span>  
 [<span data-ttu-id="3e6d4-109">O modelo de objeto LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="3e6d4-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="3e6d4-110">Como personalizar classes de entidade usando o Editor de código</span><span class="sxs-lookup"><span data-stu-id="3e6d4-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
