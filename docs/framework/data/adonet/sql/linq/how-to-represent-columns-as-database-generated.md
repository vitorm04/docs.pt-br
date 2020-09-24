---
title: 'Como: declarar colunas como geradas por banco de dados'
ms.date: 03/30/2017
ms.assetid: 6524b8a6-e5d2-4a3b-8e08-beafc4a84fd2
ms.openlocfilehash: 914fdcb78efbaaddf08330e32e1d7f7c4e62436e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166307"
---
# <a name="how-to-represent-columns-as-database-generated"></a><span data-ttu-id="aa8cd-102">Como: declarar colunas como geradas por banco de dados</span><span class="sxs-lookup"><span data-stu-id="aa8cd-102">How to: Represent Columns as Database-Generated</span></span>

<span data-ttu-id="aa8cd-103">Use a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> propriedade no <xref:System.Data.Linq.Mapping.ColumnAttribute> atributo para designar um campo ou propriedade como representando uma coluna gerada pelo banco de dados.</span><span class="sxs-lookup"><span data-stu-id="aa8cd-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database-generated column.</span></span>  
  
 <span data-ttu-id="aa8cd-104">Para exemplos de código, consulte <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span><span class="sxs-lookup"><span data-stu-id="aa8cd-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-database-generated-column"></a><span data-ttu-id="aa8cd-105">Para designar um campo ou propriedade como a representação de uma coluna base de dados - gerado</span><span class="sxs-lookup"><span data-stu-id="aa8cd-105">To designate a field or property as representing a database-generated column</span></span>  
  
1. <span data-ttu-id="aa8cd-106">Adicione a propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> ao atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> .</span><span class="sxs-lookup"><span data-stu-id="aa8cd-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="aa8cd-107">Defina o valor da propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="aa8cd-107">Set the property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa8cd-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="aa8cd-108">See also</span></span>

- [<span data-ttu-id="aa8cd-109">Modelo de objeto LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="aa8cd-109">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="aa8cd-110">Como: personalizar classes de entidade usando o editor de códigos</span><span class="sxs-lookup"><span data-stu-id="aa8cd-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
