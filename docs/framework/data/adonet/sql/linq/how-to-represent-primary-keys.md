---
title: 'Como: Representar chaves primárias'
ms.date: 03/30/2017
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
ms.openlocfilehash: a7cea40b30243c6b15da0500a59ba801f2c8da68
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687421"
---
# <a name="how-to-represent-primary-keys"></a><span data-ttu-id="91c05-102">Como: Representar chaves primárias</span><span class="sxs-lookup"><span data-stu-id="91c05-102">How to: Represent Primary Keys</span></span>
<span data-ttu-id="91c05-103">Use o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> propriedade no <xref:System.Data.Linq.Mapping.ColumnAttribute> atributo para designar uma propriedade ou campo para representar a chave primária para uma coluna de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="91c05-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a property or field to represent the primary key for a database column.</span></span>  
  
 <span data-ttu-id="91c05-104">Para exemplos de código, consulte <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="91c05-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="91c05-105">não suporta colunas computadas como chaves primárias.</span><span class="sxs-lookup"><span data-stu-id="91c05-105">does not support computed columns as primary keys.</span></span>  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a><span data-ttu-id="91c05-106">Para designar uma propriedade ou um campo como uma chave primária</span><span class="sxs-lookup"><span data-stu-id="91c05-106">To designate a property or field as a primary key</span></span>  
  
1.  <span data-ttu-id="91c05-107">Adicione a propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> ao atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> .</span><span class="sxs-lookup"><span data-stu-id="91c05-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="91c05-108">Especificar o valor como `true`.</span><span class="sxs-lookup"><span data-stu-id="91c05-108">Specify the value as `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91c05-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91c05-109">See also</span></span>
- [<span data-ttu-id="91c05-110">O modelo de objeto LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="91c05-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="91c05-111">Como: Personalizar Classes de entidade usando o Editor de código</span><span class="sxs-lookup"><span data-stu-id="91c05-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
