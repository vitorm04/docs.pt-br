---
title: 'Como: declarar colunas com permissão de valores nulos'
ms.date: 03/30/2017
ms.assetid: ebb71a37-1f4c-4fa7-b2d2-d903f13c4af1
ms.openlocfilehash: 00a837467010c2d8a9f0ca16d6aba2fc5f4c973f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781814"
---
# <a name="how-to-represent-columns-as-allowing-null-values"></a><span data-ttu-id="ff76e-102">Como: declarar colunas com permissão de valores nulos</span><span class="sxs-lookup"><span data-stu-id="ff76e-102">How to: Represent Columns as Allowing Null Values</span></span>
<span data-ttu-id="ff76e-103">Use a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> propriedade no<xref:System.Data.Linq.Mapping.ColumnAttribute> atributo para especificar que a coluna de banco de dados associada pode conter valores nulos.</span><span class="sxs-lookup"><span data-stu-id="ff76e-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify that the associated database column can hold null values.</span></span>  
  
 <span data-ttu-id="ff76e-104">Para exemplos de código, consulte <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span><span class="sxs-lookup"><span data-stu-id="ff76e-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span></span>  
  
### <a name="to-designate-a-column-as-allowing-null-values"></a><span data-ttu-id="ff76e-105">Para designar uma coluna como permitir valores nulos</span><span class="sxs-lookup"><span data-stu-id="ff76e-105">To designate a column as allowing null values</span></span>  
  
1. <span data-ttu-id="ff76e-106">Adicione a propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> ao atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> .</span><span class="sxs-lookup"><span data-stu-id="ff76e-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="ff76e-107">Definir o valor da propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> a `true`.</span><span class="sxs-lookup"><span data-stu-id="ff76e-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff76e-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ff76e-108">See also</span></span>

- [<span data-ttu-id="ff76e-109">O modelo de objeto LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="ff76e-109">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="ff76e-110">Como: Personalizar classes de entidade usando o editor de código</span><span class="sxs-lookup"><span data-stu-id="ff76e-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
