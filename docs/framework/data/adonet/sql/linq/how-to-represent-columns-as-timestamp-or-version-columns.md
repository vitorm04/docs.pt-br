---
title: 'Como: Representa colunas como colunas de carimbo de data/hora ou a versão'
ms.date: 03/30/2017
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
ms.openlocfilehash: 2fc8aaf260dc3657e33e539939fdf58ad8224c93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361233"
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a><span data-ttu-id="1f3f3-102">Como: Representa colunas como colunas de carimbo de data/hora ou a versão</span><span class="sxs-lookup"><span data-stu-id="1f3f3-102">How to: Represent Columns as Timestamp or Version Columns</span></span>
<span data-ttu-id="1f3f3-103">Use o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> propriedade o <xref:System.Data.Linq.Mapping.ColumnAttribute> atributo para designar um campo ou propriedade como representando uma coluna de banco de dados que contém números de versão ou os carimbos de hora do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="1f3f3-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property of the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database column that holds database timestamps or version numbers.</span></span>  
  
 <span data-ttu-id="1f3f3-104">Para exemplos de código, consulte <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="1f3f3-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a><span data-ttu-id="1f3f3-105">Para designar um campo ou propriedade como a representação de uma coluna de carimbo de data/hora ou a versão</span><span class="sxs-lookup"><span data-stu-id="1f3f3-105">To designate a field or property as representing a timestamp or version column</span></span>  
  
1.  <span data-ttu-id="1f3f3-106">Adicione a propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> ao atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> .</span><span class="sxs-lookup"><span data-stu-id="1f3f3-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="1f3f3-107">Definir o valor da propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> a `true`.</span><span class="sxs-lookup"><span data-stu-id="1f3f3-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f3f3-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1f3f3-108">See Also</span></span>  
 [<span data-ttu-id="1f3f3-109">O modelo de objeto LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="1f3f3-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="1f3f3-110">Como especificar quais membros são testados quanto a conflitos de simultaneidade</span><span class="sxs-lookup"><span data-stu-id="1f3f3-110">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)  
 [<span data-ttu-id="1f3f3-111">Como personalizar classes de entidade usando o Editor de código</span><span class="sxs-lookup"><span data-stu-id="1f3f3-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
