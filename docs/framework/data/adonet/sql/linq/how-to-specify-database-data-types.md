---
title: 'Como: Especificar tipos de dados de base de dados'
ms.date: 03/30/2017
ms.assetid: 2228fdad-7e6a-4b1b-b4d1-79d0198b7c28
ms.openlocfilehash: 6b13af9be0fd3b10b4849694134b8cf8290a8dfb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360661"
---
# <a name="how-to-specify-database-data-types"></a><span data-ttu-id="9a7cf-102">Como: Especificar tipos de dados de base de dados</span><span class="sxs-lookup"><span data-stu-id="9a7cf-102">How to: Specify Database Data Types</span></span>
<span data-ttu-id="9a7cf-103">Use o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> propriedade em um <xref:System.Data.Linq.Mapping.ColumnAttribute> atributo para especificar o texto exato que define a coluna em uma declaração de tabela T-SQL.</span><span class="sxs-lookup"><span data-stu-id="9a7cf-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify the exact text that defines the column in a T-SQL table declaration.</span></span>  
  
 <span data-ttu-id="9a7cf-104">Você deve especificar a propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> somente se você planejar usar <xref:System.Data.Linq.DataContext.CreateDatabase%2A> para criar uma instância de base de dados.</span><span class="sxs-lookup"><span data-stu-id="9a7cf-104">You must specify the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property only if you plan to use <xref:System.Data.Linq.DataContext.CreateDatabase%2A> to create an instance of the database.</span></span>  
  
 <span data-ttu-id="9a7cf-105">Para exemplos de código, consulte <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span><span class="sxs-lookup"><span data-stu-id="9a7cf-105">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span></span>  
  
### <a name="to-specify-text-to-define-a-data-type-in-a-t-sql-table"></a><span data-ttu-id="9a7cf-106">Para especificar o texto para definir um tipo de dados em uma tabela T-SQL</span><span class="sxs-lookup"><span data-stu-id="9a7cf-106">To specify text to define a data type in a T-SQL table</span></span>  
  
1.  <span data-ttu-id="9a7cf-107">Adicione a propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> ao atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> .</span><span class="sxs-lookup"><span data-stu-id="9a7cf-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="9a7cf-108">Defina o valor da propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> ao texto exato que é usado por T-SQL.</span><span class="sxs-lookup"><span data-stu-id="9a7cf-108">Set the value of the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the exact text that is used by T-SQL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a7cf-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9a7cf-109">See Also</span></span>  
 [<span data-ttu-id="9a7cf-110">O modelo de objeto LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="9a7cf-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="9a7cf-111">Como personalizar classes de entidade usando o Editor de código</span><span class="sxs-lookup"><span data-stu-id="9a7cf-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
