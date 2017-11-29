---
title: 'Como: Representa colunas como Base de dados - gerados'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6524b8a6-e5d2-4a3b-8e08-beafc4a84fd2
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a0b36e7035b885985e70203146957cdfca92148b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-represent-columns-as-database-generated"></a><span data-ttu-id="ed926-102">Como: Representa colunas como Base de dados - gerados</span><span class="sxs-lookup"><span data-stu-id="ed926-102">How to: Represent Columns as Database-Generated</span></span>
<span data-ttu-id="ed926-103">Use o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> propriedade o <xref:System.Data.Linq.Mapping.ColumnAttribute> atributo para designar um campo ou propriedade como representando uma coluna de banco de dados gerado.</span><span class="sxs-lookup"><span data-stu-id="ed926-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database-generated column.</span></span>  
  
 <span data-ttu-id="ed926-104">Para exemplos de código, consulte <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span><span class="sxs-lookup"><span data-stu-id="ed926-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-database-generated-column"></a><span data-ttu-id="ed926-105">Para designar um campo ou propriedade como a representação de uma coluna base de dados - gerado</span><span class="sxs-lookup"><span data-stu-id="ed926-105">To designate a field or property as representing a database-generated column</span></span>  
  
1.  <span data-ttu-id="ed926-106">Adicione a propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> ao atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> .</span><span class="sxs-lookup"><span data-stu-id="ed926-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="ed926-107">Defina o valor da propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="ed926-107">Set the property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed926-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ed926-108">See Also</span></span>  
 [<span data-ttu-id="ed926-109">O LINQ no modelo de objeto do SQL</span><span class="sxs-lookup"><span data-stu-id="ed926-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="ed926-110">Como: Personalizar Classes de entidade usando o Editor de código</span><span class="sxs-lookup"><span data-stu-id="ed926-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
