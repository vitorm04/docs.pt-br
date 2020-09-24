---
title: 'Como: declarar chaves primárias'
ms.date: 03/30/2017
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
ms.openlocfilehash: 02570176c8aef5cfdc7ba09fd6976f430900e8df
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166229"
---
# <a name="how-to-represent-primary-keys"></a><span data-ttu-id="43277-102">Como: declarar chaves primárias</span><span class="sxs-lookup"><span data-stu-id="43277-102">How to: Represent Primary Keys</span></span>

<span data-ttu-id="43277-103">Use a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> propriedade no <xref:System.Data.Linq.Mapping.ColumnAttribute> atributo para designar uma propriedade ou campo para representar a chave primária para uma coluna de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="43277-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a property or field to represent the primary key for a database column.</span></span>  
  
 <span data-ttu-id="43277-104">Para exemplos de código, consulte <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="43277-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="43277-105">não suporta colunas computadas como chaves primárias.</span><span class="sxs-lookup"><span data-stu-id="43277-105">does not support computed columns as primary keys.</span></span>  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a><span data-ttu-id="43277-106">Para designar uma propriedade ou um campo como uma chave primária</span><span class="sxs-lookup"><span data-stu-id="43277-106">To designate a property or field as a primary key</span></span>  
  
1. <span data-ttu-id="43277-107">Adicione a propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> ao atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> .</span><span class="sxs-lookup"><span data-stu-id="43277-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="43277-108">Especificar o valor como `true`.</span><span class="sxs-lookup"><span data-stu-id="43277-108">Specify the value as `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43277-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="43277-109">See also</span></span>

- [<span data-ttu-id="43277-110">Modelo de objeto LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="43277-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="43277-111">Como: personalizar classes de entidade usando o editor de códigos</span><span class="sxs-lookup"><span data-stu-id="43277-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
