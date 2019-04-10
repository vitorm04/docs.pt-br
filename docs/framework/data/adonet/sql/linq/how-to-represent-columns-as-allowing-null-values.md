---
title: 'Como: declarar colunas com permissão de valores nulos'
ms.date: 03/30/2017
ms.assetid: ebb71a37-1f4c-4fa7-b2d2-d903f13c4af1
ms.openlocfilehash: ef8fa87963b91ef7140fbaefb657fc7904604b5b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331150"
---
# <a name="how-to-represent-columns-as-allowing-null-values"></a><span data-ttu-id="aa3c0-102">Como: declarar colunas com permissão de valores nulos</span><span class="sxs-lookup"><span data-stu-id="aa3c0-102">How to: Represent Columns as Allowing Null Values</span></span>
<span data-ttu-id="aa3c0-103">Use o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> propriedade no <xref:System.Data.Linq.Mapping.ColumnAttribute> atributo para especificar que a coluna de banco de dados associado pode conter valores nulos.</span><span class="sxs-lookup"><span data-stu-id="aa3c0-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify that the associated database column can hold null values.</span></span>  
  
 <span data-ttu-id="aa3c0-104">Para exemplos de código, consulte <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span><span class="sxs-lookup"><span data-stu-id="aa3c0-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span></span>  
  
### <a name="to-designate-a-column-as-allowing-null-values"></a><span data-ttu-id="aa3c0-105">Para designar uma coluna como permitir valores nulos</span><span class="sxs-lookup"><span data-stu-id="aa3c0-105">To designate a column as allowing null values</span></span>  
  
1. <span data-ttu-id="aa3c0-106">Adicione a propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> ao atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> .</span><span class="sxs-lookup"><span data-stu-id="aa3c0-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="aa3c0-107">Definir o valor da propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> a `true`.</span><span class="sxs-lookup"><span data-stu-id="aa3c0-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa3c0-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa3c0-108">See also</span></span>

- [<span data-ttu-id="aa3c0-109">Modelo de objeto LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="aa3c0-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="aa3c0-110">Como: personalizar classes de entidade usando o editor de códigos</span><span class="sxs-lookup"><span data-stu-id="aa3c0-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
