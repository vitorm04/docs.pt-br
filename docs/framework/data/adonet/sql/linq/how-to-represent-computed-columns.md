---
title: 'Como: declarar colunas computadas'
ms.date: 03/30/2017
ms.assetid: 4025f1fd-9dfa-46c0-b04f-34e8bc7957a2
ms.openlocfilehash: 01c3442448285893ebb476ed11889e073065d4d8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943541"
---
# <a name="how-to-represent-computed-columns"></a><span data-ttu-id="af4a0-102">Como: declarar colunas computadas</span><span class="sxs-lookup"><span data-stu-id="af4a0-102">How to: Represent Computed Columns</span></span>
<span data-ttu-id="af4a0-103">Use a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> Propriedade em um <xref:System.Data.Linq.Mapping.ColumnAttribute> atributo para representar uma coluna cujo conteúdo é o resultado do cálculo.</span><span class="sxs-lookup"><span data-stu-id="af4a0-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to represent a column whose contents are the result of calculation.</span></span>  
  
 <span data-ttu-id="af4a0-104">Para exemplos de código, consulte <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span><span class="sxs-lookup"><span data-stu-id="af4a0-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="af4a0-105">não suporta colunas computadas como chaves primárias.</span><span class="sxs-lookup"><span data-stu-id="af4a0-105">does not support computed columns as primary keys.</span></span>  
  
### <a name="to-represent-a-computed-column"></a><span data-ttu-id="af4a0-106">Para representar uma coluna computado</span><span class="sxs-lookup"><span data-stu-id="af4a0-106">To represent a computed column</span></span>  
  
1. <span data-ttu-id="af4a0-107">Adicione a propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> ao atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> .</span><span class="sxs-lookup"><span data-stu-id="af4a0-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="af4a0-108">Atribuir uma representação de cadeia de caracteres de fórmula à propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> .</span><span class="sxs-lookup"><span data-stu-id="af4a0-108">Assign a string representation of the formula to the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af4a0-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af4a0-109">See also</span></span>

- [<span data-ttu-id="af4a0-110">O modelo de objeto LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="af4a0-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="af4a0-111">Como: Personalizar classes de entidade usando o editor de código</span><span class="sxs-lookup"><span data-stu-id="af4a0-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
