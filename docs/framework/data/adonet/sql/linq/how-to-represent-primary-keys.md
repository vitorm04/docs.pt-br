---
title: "Como: Representa chaves primárias"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3510d52f6f6de9ee2e99ebc1e9fc6fa581d58f3f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-represent-primary-keys"></a><span data-ttu-id="6de21-102">Como: Representa chaves primárias</span><span class="sxs-lookup"><span data-stu-id="6de21-102">How to: Represent Primary Keys</span></span>
<span data-ttu-id="6de21-103">Use o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> propriedade o <xref:System.Data.Linq.Mapping.ColumnAttribute> atributo para designar uma propriedade ou campo para representar a chave primária para uma coluna de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="6de21-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a property or field to represent the primary key for a database column.</span></span>  
  
 <span data-ttu-id="6de21-104">Para exemplos de código, consulte <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="6de21-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="6de21-105"> não suporta colunas computadas como chaves primárias.</span><span class="sxs-lookup"><span data-stu-id="6de21-105"> does not support computed columns as primary keys.</span></span>  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a><span data-ttu-id="6de21-106">Para designar uma propriedade ou um campo como uma chave primária</span><span class="sxs-lookup"><span data-stu-id="6de21-106">To designate a property or field as a primary key</span></span>  
  
1.  <span data-ttu-id="6de21-107">Adicione a propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> ao atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> .</span><span class="sxs-lookup"><span data-stu-id="6de21-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="6de21-108">Especificar o valor como `true`.</span><span class="sxs-lookup"><span data-stu-id="6de21-108">Specify the value as `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6de21-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6de21-109">See Also</span></span>  
 [<span data-ttu-id="6de21-110">O LINQ no modelo de objeto do SQL</span><span class="sxs-lookup"><span data-stu-id="6de21-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="6de21-111">Como: Personalizar Classes de entidade usando o Editor de código</span><span class="sxs-lookup"><span data-stu-id="6de21-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
