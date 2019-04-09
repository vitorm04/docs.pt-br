---
title: 'Como: declarar colunas como geradas por banco de dados'
ms.date: 03/30/2017
ms.assetid: 6524b8a6-e5d2-4a3b-8e08-beafc4a84fd2
ms.openlocfilehash: 2fca0c2fb1d28b5e83902f8664d1c7331774718b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148246"
---
# <a name="how-to-represent-columns-as-database-generated"></a><span data-ttu-id="3d1be-102">Como: declarar colunas como geradas por banco de dados</span><span class="sxs-lookup"><span data-stu-id="3d1be-102">How to: Represent Columns as Database-Generated</span></span>
<span data-ttu-id="3d1be-103">Use o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> propriedade no <xref:System.Data.Linq.Mapping.ColumnAttribute> atributo para designar um campo ou propriedade como a representação de uma coluna de banco de dados gerado.</span><span class="sxs-lookup"><span data-stu-id="3d1be-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database-generated column.</span></span>  
  
 <span data-ttu-id="3d1be-104">Para exemplos de código, consulte <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span><span class="sxs-lookup"><span data-stu-id="3d1be-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-database-generated-column"></a><span data-ttu-id="3d1be-105">Para designar um campo ou propriedade como a representação de uma coluna base de dados - gerado</span><span class="sxs-lookup"><span data-stu-id="3d1be-105">To designate a field or property as representing a database-generated column</span></span>  
  
1.  <span data-ttu-id="3d1be-106">Adicione a propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> ao atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> .</span><span class="sxs-lookup"><span data-stu-id="3d1be-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="3d1be-107">Defina o valor da propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="3d1be-107">Set the property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d1be-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3d1be-108">See also</span></span>

- [<span data-ttu-id="3d1be-109">Modelo de objeto LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="3d1be-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="3d1be-110">Como: personalizar classes de entidade usando o editor de códigos</span><span class="sxs-lookup"><span data-stu-id="3d1be-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
