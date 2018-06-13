---
title: 'Como: Representa colunas como Base de dados - gerados'
ms.date: 03/30/2017
ms.assetid: 6524b8a6-e5d2-4a3b-8e08-beafc4a84fd2
ms.openlocfilehash: f6b127208ae359b43f273f54d7b5c72933c2eba6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353728"
---
# <a name="how-to-represent-columns-as-database-generated"></a><span data-ttu-id="a39c2-102">Como: Representa colunas como Base de dados - gerados</span><span class="sxs-lookup"><span data-stu-id="a39c2-102">How to: Represent Columns as Database-Generated</span></span>
<span data-ttu-id="a39c2-103">Use o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> propriedade o <xref:System.Data.Linq.Mapping.ColumnAttribute> atributo para designar um campo ou propriedade como representando uma coluna de banco de dados gerado.</span><span class="sxs-lookup"><span data-stu-id="a39c2-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database-generated column.</span></span>  
  
 <span data-ttu-id="a39c2-104">Para exemplos de código, consulte <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span><span class="sxs-lookup"><span data-stu-id="a39c2-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-database-generated-column"></a><span data-ttu-id="a39c2-105">Para designar um campo ou propriedade como a representação de uma coluna base de dados - gerado</span><span class="sxs-lookup"><span data-stu-id="a39c2-105">To designate a field or property as representing a database-generated column</span></span>  
  
1.  <span data-ttu-id="a39c2-106">Adicione a propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> ao atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> .</span><span class="sxs-lookup"><span data-stu-id="a39c2-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="a39c2-107">Defina o valor da propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="a39c2-107">Set the property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a39c2-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a39c2-108">See Also</span></span>  
 [<span data-ttu-id="a39c2-109">O modelo de objeto LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="a39c2-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="a39c2-110">Como personalizar classes de entidade usando o Editor de código</span><span class="sxs-lookup"><span data-stu-id="a39c2-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
